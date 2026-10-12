# Rapport de Test : TC-BUS-02

**Titre :** Calcul du sous-total multi-articles  
**Catégorie :** Règle Métier  
**Statut :** PASS  
**Date d'exécution :** 28 septembre 2026  
**Exécuté par :** Kavisha — QA Tester  

---

## 1. Objectif
Valider la formule de calcul du sous-total lors du cumul de plusieurs produits en quantités variées.

## 2. Préconditions
* Panier ouvert.

## 3. Étapes d'exécution
1. Ajouter 2 x Plat A (10,00 € l'unité).
2. Ajouter 1 x Plat B (5,00 € l'unité).
3. Vérifier le sous-total.

## 4. Résultat attendu
Sous-total = `(2 * 10,00) + (1 * 5,00) = 25,00 €`.

## 5. Résultat obtenu
Sous-total calculé exactement à 25,00 €.

## 6. Preuve visuelle
![Preuve TC-BUS-02](../../screenshots/TC-BUS/TC-BUS-02.png)