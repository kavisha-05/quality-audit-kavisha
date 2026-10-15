# Cahier de Tests & Résultats d'Exécution — QuickOrder

**Projet :** Audit Qualité QuickOrder  
**Date :** 28 septembre 2026  
**Auteure :** Kavisha — QA Tester  
**Environnement :** Docker (Flask / PostgreSQL / Mailpit) — `http://127.0.0.1:5000`  
**Total des tests :** 24 cas de test (17 Pass / 7 Fail)  

##  Bilan Global de l'Exécution

| Catégorie | Total | Succès (PASS) | Échecs (FAIL) |
| :--- | :---: | :---: | :---: |
| **Nominal (TC-NOM)** | 6 | 6 | 0 |
| **Limites (TC-LIM)** | 6 | 3 | 3 |
| **Erreurs (TC-ERR)** | 6 | 6 | 0 |
| **Règles Métier (TC-BUS)** | 6 | 1 | 5 |
| **TOTAL** | **24** | **16** | **8** |


##  Liste Détillée des Cas de Test

### 1. Tests Nominaux (`TC-NOM`)
* [TC-NOM-01](./test-cases/TC-NOM-01.md) — Santé de l'API & Disponibilité (`PASS`)
* [TC-NOM-02](./test-cases/TC-NOM-02.md) — Navigation sur la liste des restaurants (`PASS`)
* [TC-NOM-03](./test-cases/TC-NOM-03.md) — Authentification et affichage du profil (`PASS`)
* [TC-NOM-04](./test-cases/TC-NOM-04.md) — Consultation du menu d'un restaurant (`PASS`)
* [TC-NOM-05](./test-cases/TC-NOM-05.md) — Ajout de produits et gestion du panier (`PASS`)
* [TC-NOM-06](./test-cases/TC-NOM-06.md) — Consultation de la liste des restaurants via l'API Swagger (PASS)

### 2. Tests aux Limites (`TC-LIM`)
* [TC-LIM-01](./test-cases/TC-LIM-01.md) — Saisie de la quantité maximale (99 unités) (`PASS`)
* [TC-LIM-02](./test-cases/TC-LIM-02.md) — Commande au montant sous le seuil minimum (`FAIL` ➔ `BUG-001`)
* [TC-LIM-03](./test-cases/TC-LIM-03.md) — Saisie d'une adresse de livraison très longue (`PASS`)
* [TC-LIM-04](./test-cases/TC-LIM-04.md) — Paramètre de limite API `limit=0` (`FAIL` ➔ `BUG-002`)
* [TC-LIM-05](./test-cases/TC-LIM-05.md) — Recherche par chaîne de caractères minimale (`PASS`)
* [TC-LIM-06](./test-cases/TC-LIM-06.md) — Saisie de caractères spéciaux et injection XSS (`PASS` ➔ `BUG-006`)

### 3. Tests d'Erreurs (`TC-ERR`)
* [TC-ERR-01](./test-cases/TC-ERR-01.md) — Commande sur un restaurant fermé (`FAIL` ➔ `BUG-004`)
* [TC-ERR-02](./test-cases/TC-ERR-02.md) — Gestion de la perte de connexion réseau (`PASS`)
* [TC-ERR-03](./test-cases/TC-ERR-03.md) — Saisie d'un code promo inexistant ou expiré (`PASS`)
* [TC-ERR-04](./test-cases/TC-ERR-04.md) — Authentification API avec une clé invalide (`PASS`)
* [TC-ERR-05](./test-cases/TC-ERR-05.md) — Validation de commande avec un panier vide (`PASS`)
* [TC-ERR-06](./test-cases/TC-ERR-06.md) — Appel API sur une ressource inexistante 404 (`FAIL` ➔ `BUG-007`)

### 4. Tests Règles Métier (`TC-BUS`)
* [TC-BUS-01](./test-cases/TC-BUS-01.md) — Application conforme des frais de livraison (`PASS`)
* [TC-BUS-02](./test-cases/TC-BUS-02.md) — Calcul exact du sous-total multi-articles (`PASS`)
* [TC-BUS-03](./test-cases/TC-BUS-03.md) — Règle du panier unique par restaurant (`PASS`)
* [TC-BUS-04](./test-cases/TC-BUS-04.md) — Non-respect du minimum de commande restaurant (`FAIL` ➔ `BUG-001`)
* [TC-BUS-05](./test-cases/TC-BUS-05.md) — Commande d'un article marqué Hors Stock (`FAIL` ➔ `BUG-005`)
* [TC-BUS-06](./test-cases/TC-BUS-06.md) — Calcul erroné de la réduction sur code promo (`FAIL` ➔ `BUG-003`)