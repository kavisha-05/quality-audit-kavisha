# Rapport de Test : TC-LIM-04

**Titre :** Contrôle du paramètre de pagination API `limit=0`  
**Catégorie :** Limite / API REST  
**Statut :** FAIL  
**Date d'exécution :** 28 septembre 2026  
**Anomalie associée :** BUG-002  

---

## 1. Objectif
Tester le comportement de l'endpoint `/api/restaurants` lorsqu'un paramètre de limite nul (`limit=0`) est transmis.

## 2. Préconditions
* API QuickOrder accessible (`http://127.0.0.1:5000`).
* Clé API valide (`quickorder-demo-key`).

## 3. Étapes d'exécution
1. Ouvrir le terminal MINGW64 / Git Bash.
2. Exécuter la commande cURL suivante :
   `curl -X GET "http://127.0.0.1:5000/api/restaurants?limit=0" -H "X-API-Key: quickorder-demo-key"`
3. Analyser la réponse JSON.

## 4. Résultat attendu
L'API doit retourner une liste vide (`"items": []`) ou renvoyer un code HTTP `400 Bad Request` signalant une limite invalide.

## 5. Résultat obtenu
L'API ignore le paramètre `limit=0` et renvoie la totalité des 6 restaurants enregistrés (`"count": 6`).

## 6. Preuve visuelle
![Preuve TC-LIM-04](../../screenshots/TC-LIM/TC-LIM-04.png)