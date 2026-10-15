# Rapport de Test : TC-NOM-06

**Titre :** Consultation de la liste des restaurants via l'API Swagger  
**Catégorie :** Nominal  
**Statut :** PASS   
**Date d'exécution :** 28 septembre 2026  
**Exécuté par :** Kavisha — QA Tester  

---

## 1. Objectif
Valider la récupération correcte de la liste des restaurants via l'API backend en utilisant l'interface Swagger avec une authentification valide.

## 2. Préconditions
- Application backend et interface Swagger accessibles.
- Clé d'authentification valide (`X-API-Key`) disponible.

## 3. Étapes d'exécution
1. Ouvrir l'interface Swagger de l'API.
2. Cliquer sur "Authorize" et renseigner la clé API (`X-API-Key: quickorder-demo-key`).
3. Déplier l'endpoint `GET /api/restaurants` et cliquer sur "Try it out".
4. Cliquer sur "Execute" pour lancer la requête.

## 4. Résultat attendu
Le serveur renvoie un code de statut HTTP 200 OK ainsi qu'au format JSON la liste complète des restaurants enregistrés dans la base de données.

## 5. Résultat obtenu
Requête exécutée avec succès : code HTTP 200 renvoyé et affichage de la liste JSON des restaurants.

## 6. Preuve visuelle
![Preuve TC-NOM-06 - Swagger Authorize](../../screenshots/TC-NOM/TC-NOM-06-1.png)
![Preuve TC-NOM-06 - Execution API](../../screenshots/TC-NOM/TC-NOM-06-2.png)
![Preuve TC-NOM-06 - Réponse HTTP 200](../../screenshots/TC-NOM/TC-NOM-06-3.png)
![Preuve TC-NOM-06 - Confirmation finale](../../screenshots/TC-NOM/TC-NOM-06-4.png)