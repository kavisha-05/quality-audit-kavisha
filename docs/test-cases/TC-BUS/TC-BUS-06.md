# Rapport de Test : TC-BUS-06

**Titre :** Calcul et application d'un code promo valide (`ATLAS15`)  
**Catégorie :** Règle Métier  
**Statut :** FAIL   
**Date d'exécution :** 28 septembre 2026  
**Anomalie associée :** BUG-003  

---

## 1. Objectif
Vérifier que l'application d'un code promo de réduction en pourcentage (ex: `ATLAS15` offrant 15% de remise) calcule exactement la remise sur le sous-total.

## 2. Préconditions
* Panier validé chez Couscous Atlas pour un sous-total de 24,90 €.
* Frais de livraison : 2,99 €.

## 3. Étapes d'exécution
1. Saisir le code promo `ATLAS15` sur la page de paiement.
2. Cliquer sur "Appliquer".
3. Vérifier le montant figurant sur la ligne "Réduction".

## 4. Résultat attendu
15% de 24,90 € représente une déduction exacte de **3,73 €** (Total final attendu : 24,16 €).

## 5. Résultat obtenu
Le système applique une réduction de **-2,49 €** (qui correspond au montant des frais de livraison au lieu des 15% du sous-total), produisant un total erroné de 25,40 €.

## 6. Preuve visuelle
![Preuve TC-BUS-06](../../screenshots/TC-BUS/TC-BUS-06.png)