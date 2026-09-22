# Stratégie de Test — QuickOrder

## 1. Contexte & Objectif
QuickOrder est une plateforme de livraison de repas composée d'une interface Web utilisateur et d'une API REST backend. 
L'objectif de cette campagne est d'évaluer la qualité globale du système, d'identifier les anomalies critiques et d'émettre une recommandation d'opportunité de mise en production (Go / No-Go).

---

## 2. Périmètre de Test

### 2.1 Dans le périmètre (In-Scope)
* **Interface Web Frontend (`http://127.0.0.1:5000`) :**
  * Catalogue des restaurants, filtres et statuts (ouvert/fermé).
  * Fiches produits et gestion des stocks (disponible/hors stock).
  * Panier, calculs des prix, réductions et frais de livraison.
  * Tunnel de commande et confirmation.
  * Espace profil utilisateur.
* **API REST Backend (`http://127.0.0.1:5000/docs`) :**
  * Authentification API (`X-API-Key`).
  * Endpoints de santé (`/health`), des restaurants (`/restaurants`) et des commandes (`/orders`).
  * Cohérence des données renvoyées (formats JSON, codes de statut HTTP).

### 2.2 Hors périmètre (Out-of-Scope)
* Tests de charge et de haute disponibilité (Performance/Stress).
* Tests de sécurité avancés (pen-testing, injection SQL poussée).
* Systèmes tiers de paiement réel (utilisation de stubs / simulations).

---

## 3. Parcours Critiques Identifiés
1. **Consulter et choisir :** Inscription/Connexion client → Sélection d'un restaurant ouvert → Ajout d'articles en stock.
2. **Commander et payer :** Vérification du panier → Application des frais de livraison → Validation et confirmation de la commande.
3. **Flux API :** Authentification via `X-API-Key` → Récupération des ressources backend.

---

## 4. Typologie des Tests & Répartition (24 Cas de Test)
* **6 Cas Nominaux :** Scénarios d'usage courant sans erreur.
* **6 Cas Limites :** Saisie de valeurs extrêmes, seuils minimums, longueurs de champs.
* **6 Cas d'Erreur :** Saisies invalides, absence de clé API, requêtes malformées.
* **6 Cas de Règles Métier :** Produits hors stock, restaurants fermés, calcul exact du panier (`Sous-total + Livraison = Total`).

---

## 5. Environnement & Outils
* **Navigateurs :** Chrome / Firefox / Edge.
* **Outils d'analyse :** Chrome DevTools (Inspecteur, Console JS, Onglet Réseau).
* **Outils API :** Swagger UI, cURL, Postman / Bruno.
* **Gestion des anomalies :** Repository Git `quality-audit-kavisha`.