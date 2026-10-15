# Rapport de Test : TC-NOM-02

**Titre :** Inscription d'un nouvel utilisateur  
**Catégorie :** Nominal  
**Statut :** PASS  
**Date d'exécution :** 28 septembre 2026  
**Exécuté par :** Kavisha — QA Tester  

---

## 1. Objectif
Valider la création d'un nouveau compte client à partir du formulaire d'inscription.

## 2. Préconditions
* Utilisateur non connecté.
* Adresse e-mail de test non existante en BDD (`test.user@example.com`).

## 3. Étapes d'exécution
1. Cliquer sur le lien "Inscription" dans le header.
2. Saisir un nom complet, une adresse e-mail valide et un mot de passe sécurisé.
3. Cliquer sur le bouton "S'inscrire".

## 4. Résultat attendu
Le compte est créé en BDD, un message de confirmation apparaît et l'utilisateur est redirigé vers la page de connexion ou automatiquement connecté.

## 5. Résultat obtenu
Inscription réussie, l'utilisateur est redirigé et le compte est correctement inséré dans la table `users`.

## 6. Preuve visuelle
![Preuve TC-NOM-02](../../screenshots/TC-NOM/TC-NOM-02.png)
