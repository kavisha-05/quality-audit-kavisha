# Matrice de Risques — QuickOrder

## 1. Méthodologie d'évaluation
La criticité d'un risque est calculée selon la formule : **Score = Probabilité × Impact**

* **Probabilité (1 à 3) :** 1 = Faible, 2 = Moyenne, 3 = Élevée
* **Impact (1 à 3) :** 1 = Mineur, 2 = Majeur, 3 = Critique

---

## 2. Évaluation des Risques Projet & Produit

| ID | Risque Identifié | Probabilité | Impact | Score | Sévérité | Mesure d'Atténuation (Test) |
|---|---|:---:|:---:|:---:|:---:|---|
| **R01** | Permettre la commande d'un produit marqué `HORS STOCK` | 2 | 3 | **6** | **Critique** | Test de la règle métier d'ajout au panier et validation backend lors du submit. |
| **R02** | Valider une commande auprès d'un restaurant `FERMÉ` | 2 | 3 | **6** | **Critique** | Vérification du blocage d'accès au panier / checkout pour les établissements fermés. |
| **R03** | Erreur de calcul du montant total (sous-total + livraison) | 2 | 3 | **6** | **Critique** | Vérification des règles de calcul du panier et vérification côté API REST. |
| **R04** | Vulnérabilité d'accès à l'API sans authentification (`X-API-Key`) | 2 | 3 | **6** | **Critique** | Tests d'erreur API (codes HTTP 401/403) sans header ou avec clé invalide. |
| **R05** | Mélange d'articles de deux restaurants différents dans le même panier | 3 | 2 | **6** | **Majeur** | Vérification du comportement du panier lors du changement de restaurant (vidage requis). |
| **R06** | Profil utilisateur permettant la modification vers des données invalides | 2 | 2 | **4** | **Majeur** | Tests aux limites et cas d'erreur sur le formulaire de profil (téléphone, adresse). |
| **R07** | Non-disponibilité du service backend (Panne API) | 1 | 3 | **3** | **Moyen** | Suivi du statut de l'endpoint de santé (`GET /health`). |

---

## 3. Priorisation des Campagnes
Les cas de test seront exécutés en priorité sur les risques au score le plus élevé (Score ≥ 6) afin de garantir que les parcours critiques d'achat et la sécurité API sont totalement fonctionnels avant d'envisager un Go-Live.