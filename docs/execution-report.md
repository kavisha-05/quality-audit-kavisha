# Rapport d'Exécution et d'Analyse de Campagne QA — QuickOrder

**Projet :** Audit Qualité Plateforme QuickOrder  
**Date :** 28 septembre 2026  
**Auteur :** Kavisha — QA Tester  
**Environnement :** Docker (Flask / PostgreSQL / Mailpit)  

---

## 1. Synthèse de la campagne de test

La campagne de recettes s'est déroulée sur l'ensemble des fonctionnalités clés du parcours utilisateur (Web) et des endpoints de l'API REST. Au total, **24 cas de test** ont été exécutés, répartis équitablement en 4 catégories.

### Tableau récapitulatif des résultats

| Catégorie de test | Total | Pass | Fail | Taux de réussite |
| :--- | :---: | :---: | :---: | :---: |
| **Tests Nominaux (TC-NOM)** | 6 | 6 | 0 | 100 % |
| **Tests aux Limites (TC-LIM)** | 6 | 3 | 3 | 50 % |
| **Tests d'Erreurs (TC-ERR)** | 6 | 5 | 1 | 83 % |
| **Tests Règles Métier (TC-BUS)** | 6 | 3 | 3 | 50 % |
| **TOTAL** | **24** | **17** | **7** | **70,8 %** |

---

## 2. Analyse des résultats et anomalies détectées

L'exécution a permis de remonter **8 anomalies majeures (Bug Reports)**. Bien que les parcours nominaux soient fonctionnels, des failles importantes ont été identifiées sur la sécurité et le respect des contraintes métier.

### Répartition des anomalies par sévérité

* **Critique (P0 - 2 bugs) :**
  * `BUG-004` : Prise de commande autorisée sur un restaurant affiché comme **FERMÉ** (`TC-ERR-01`).
  * `BUG-006` : Vulnérabilité **XSS Stored/Reflected** non neutralisée dans le champ d'adresse de livraison (`TC-LIM-06`).
* **Élevée (P1 - 3 bugs) :**
  * `BUG-001` : Non-respect du seuil minimum de commande imposé par le restaurant (`TC-BUS-04`).
  * `BUG-003` : Calcul erroné et incohérent du montant des réductions promotionnelles (`TC-BUS-06`).
  * `BUG-005` : Commande autorisée pour un article affiché en **Stock 0 / HORS STOCK** (`TC-BUS-05`).
* **Moyenne (P2 - 2 bugs) :**
  * `BUG-002` : Ignorance du paramètre de pagination `limit` sur l'API `/api/restaurants` (`TC-LIM-04`).
  * `BUG-008` : Écarts et incohérences d'arrondis sur les centimes du total TTC (`TC-LIM-02`).
* **Faible (P3 - 1 bug) :**
  * `BUG-007` : L'API REST renvoie du HTML au lieu de JSON sur une réponse 404 (`TC-ERR-06`).

---

## 3. Matrice des risques et impact métier

1. **Impact Financier & Juridique :**
   * Risque de perte financière liée à l'acceptation de commandes sous le seuil de rentabilité du restaurant (`BUG-001`).
   * Perte de marge à cause des erreurs de calcul de réduction (`BUG-003`) et des écarts de centimes (`BUG-008`).
2. **Impact Opérationnel :**
   * Insatisfaction client et litiges dus aux commandes passées auprès de restaurateurs fermés (`BUG-004`) ou sur des produits épuisés (`BUG-005`).
3. **Impact Sécurité & Réputation :**
   * Risque majeur de vol de session ou d'altération du DOM via la faille XSS (`BUG-006`).

---

## 4. Recommandation finale : NO-GO ❌

### Décision
Le lancement en production de la plateforme QuickOrder en l'état actuel est **STRICTEMENT DÉCONSEILLÉ (Avis NO-GO)**.

### Justification
Bien que 70,8 % des cas de test soient validés, les 2 anomalies de niveau **Critique (P0)** et les 3 anomalies de niveau **Élevé (P1)** bloquent toute mise en service commerciale.

### Conditions préalables pour lever le NO-GO :
1. **Corriger impérativement la faille de sécurité XSS (`BUG-006`)** en échappant les entrées utilisateur lors du rendu HTML.
2. **Implémenter les contrôles côté serveur** pour les règles métier bloquantes :
   * Interdire la validation panier si `statut == fermé` (`BUG-004`).
   * Interdire l'ajout au panier et le paiement d'un produit à `stock == 0` (`BUG-005`).
   * Vérifier que `sous_total >= minimum_commande` (`BUG-001`).
3. Refaire une passe de re-test (Regression testing) sur les cas `TC-BUS-04`, `TC-BUS-05`, `TC-ERR-01` et `TC-LIM-06`.