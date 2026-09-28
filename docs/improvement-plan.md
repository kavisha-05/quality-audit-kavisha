# Plan d'Amélioration et Recommandations Techniques — QuickOrder

**Date :** 28 septembre 2026  
**Évaluatrice :** Kavisha — QA Tester  
**Objectif :** Définir la feuille de route corrective pour fiabiliser la plateforme avant une future mise en production.

---

## 1. Synthèse des axes d'amélioration

L'audit QA et les retours utilisateurs mettent en évidence la nécessité d'intervenir sur 3 axes prioritaires :
1. **Sécurité & Conformité :** Neutralisation des failles et protection de l'API REST.
2. **Robustesse du moteur Métier :** Cohérence des calculs, contrôle des règles panier et gestion du stock.
3. **Ergonomie & UX :** Simplification du parcours d'achat et sécurisation des actions utilisateur.

---

## 2. Propositions d'améliorations priorisées (Plan d'action)

| N° | Domaines | Proposition d'amélioration | Justification / Impact | Priorité | Effort |
| :-: | :--- | :--- | :--- | :-: | :-: |
| **1** | **Sécurité** | Implémenter l'échappement HTML (`Sanitization`) sur l'ensemble des entrées utilisateur (adresses, profils). | Bloquer la faille XSS Stored (`BUG-006`) et sécuriser l'affichage dans le DOM. | **P0 (Urgent)** | Faible |
| **2** | **Métier** | Ajouter une validation stricte des règles métier côté serveur lors du checkout (statut ouvert/fermé, stock > 0, seuil minimum). | Empêcher la validation de commandes irréalisables (`BUG-001`, `BUG-004`, `BUG-005`). | **P0 (Urgent)** | Moyen |
| **3** | **Calcul / Finance** | Refondre le composant de calcul des prix et appliquer un arrondi bancaire standard à 2 décimales sur le total TTC. | Éliminer les écarts de centimes et fiabiliser la comptabilité (`BUG-003`, `BUG-008`). | **P1 (Élevé)** | Faible |
| **4** | **API REST** | Conformer les endpoints de l'API aux standards REST (gestion propre de `limit` et réponses d'erreur au format JSON). | Permettre une intégration tierce (ex: app mobile) sans bugs de parsing (`BUG-002`, `BUG-007`). | **P2 (Moyen)** | Faible |
| **5** | **UX / UI** | Griser les produits hors stock et masquer le bouton "Ajouter" dès la fiche du restaurant. | Éviter la frustration client lors de la sélection des plats. | **P2 (Moyen)** | Faible |
| **6** | **UX / UI** | Ajouter une modale de confirmation avant l'annulation d'une commande. | Éviter l'annulation accidentelle d'une commande en cours par l'utilisateur. | **P2 (Moyen)** | Moyen |

---

## 3. Feuille de route de déploiement (Roadmap)

### Phase 1 — Correctifs critiques & Sécurité (Sprint 1)
* Résolution de la faille XSS (`BUG-006`).
* Blocage des commandes sur restaurants fermés (`BUG-004`) et produits hors stock (`BUG-005`).
* Application stricte du montant minimum de commande (`BUG-001`).

### Phase 2 — Moteur de calcul & API (Sprint 2)
* Correction des algorithmes de réduction et des arrondis TTC (`BUG-003`, `BUG-008`).
* Normalisation des réponses d'erreur API en JSON (`BUG-007`) et fix du filtrage `limit` (`BUG-002`).

### Phase 3 — Optimisations UX & Re-test (Sprint 3)
* Mise en place des garde-fous UX (modale de confirmation, grisement hors stock).
* Campagne de **tests de non-régression (TNR)** complète sur les 24 cas de test.
* Validation finale pour lever le NO-GO.