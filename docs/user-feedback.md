# Rapport de Tests Utilisateurs (UX / Feedback) — QuickOrder

**Date :** 28 septembre 2026  
**Évaluatrice :** Kavisha — QA Tester  
**Objectif :** Évaluer l'ergonomie, la clarté et l'intuitivité de la plateforme QuickOrder auprès d'utilisateurs non-techniques.

---

## 1. Protocole de test

Deux utilisateurs aux profils variés ont testé l'application sur 3 scénarios clés :
* **Scénario 1 :** Parcourir les restaurants, choisir un plat et finaliser une commande.
* **Scénario 2 :** Appliquer un code de réduction lors de la validation du panier.
* **Scénario 3 :** Consulter l'historique des commandes et tenter d'en annuler une.

### Profils des participants
* **Utilisateur A (Alexandre) :** 24 ans, habitué des applications de livraison (Deliveroo/UberEats), profil axé sur la rapidité.
* **Utilisateur B (Chantal) :** 58 ans, peu à l'aise avec les outils numériques, recherche la clarté et la simplicité.

---

## 2. Synthèse des retours et observations

| Utilisateur | Scénario | Problème rencontré / Observation | Verbatim | Impact UX |
| :--- | :--- | :--- | :--- | :--- |
| **Utilisateur A** | Scénario 1 | Possibilité de cliquer sur des produits hors stock sans aucun avertissement visuel préalable. | *« C'est bizarre que je puisse commander un plat marqué hors stock, je m'en suis rendu compte seulement après ! »* | Élevé |
| **Utilisateur A** | Scénario 2 | Aucun retour explicite du montant économisé lors de l'application du coupon dans le récapitulatif. | *« J'ai entré le code, mais le total affiché n'a pas l'air bon par rapport aux 10%. »* | Moyen |
| **Utilisateur B** | Scénario 1 | Le bouton "Mettre à jour" du panier prête à confusion par rapport au bouton "Passer commande". | *« Je ne sais pas si je dois cliquer sur Mettre à jour ou Passer commande pour valider mes quantités. »* | Moyen |
| **Utilisateur B** | Scénario 3 | Le bouton d'annulation de commande manque de confirmation (pas de pop-up d'avertissement). | *« J'ai cliqué par erreur sur 'Annuler la commande' et ça a annulé direct sans me demander confirmation ! »* | Critique |

---

## 3. Recommandations d'améliorations UX/UI

1. **Gestion des stocks en temps réel :** Griser les boutons "+ / Ajouter" pour les produits à stock 0 et ajouter une pastille rouge explicite dès la liste des menus.
2. **Clarification du panier :** Fusionner la mise à jour automatique des quantités au changement de valeur pour supprimer le bouton "Mettre à jour" superflus.
3. **Sécurisation des actions destructives :** Ajouter une modale de confirmation (*« Êtes-vous sûr de vouloir annuler votre commande ? »*) avant de traiter l'annulation.
4. **Transparence sur les promotions :** Afficher clairement la ligne de réduction avec le montant exact déduit sous le sous-total.