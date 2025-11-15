# SAE 1.04 – Création d'une base de données et Rapport R1.02 – Dev Interface Web

## Présentation du projet

Ce dépôt contient le travail de l’équipe DataVision réalisé pour l’entreprise KDou :
- **Audit et optimisation** de la base de données (structure, cohérence, qualité)
- **Exploitation métier** via interface Access et traitements SQL complexes
- **Bilan et recommandations stratégiques** pour l’entreprise

Projet mené dans le cadre du BUT Informatique, Université Paris Cité.

## Équipe

- Axel Li
- Kenza Mokadem
- Tiago Joaquim
- Yasmine Mahfoudh

## Sommaire

- [Contexte et objectifs](#contexte-et-objectifs)
- [Mission 1 : Audit structurel et qualité des données](#mission-1--audit-structurel-et-qualité-des-données)
- [Mission 2 : Exploitation métier via Access QBE](#mission-2--exploitation-métier-via-access-qbe)
- [Mission 3 : Analyse avancée par requêtes SQL](#mission-3--analyse-avancée-par-requêtes-sql)
- [Bilan et recommandations](#bilan-et-recommandations)
- [Outils utilisés](#outils-utilisés)
- [Arborescence du dépôt](#arborescence-du-dépôt)

---

## Contexte et objectifs

KDou, entreprise de distribution alimentaire, souhaite exploiter au mieux sa base de données :
- Garantir la qualité/cohérence des données
- Faciliter l’accès pour les utilisateurs métiers
- Calculer des indicateurs stratégiques (KPI) pour orienter la décision

Trois missions complémentaires pour couvrir ces objectifs.

---

## Mission 1 : Audit structurel et qualité des données

- Analyse de la structure relationnelle (tables, clés, relations)
- Détection des incohérences et anomalies
- Recommandations pour améliorer la fiabilité

**Exemple :** validation des clients par région, identification des fournisseurs hors UE, détection de produits sans commande.

---

## Mission 2 : Exploitation métier via Access QBE

- Mise en place d’une interface graphique pour les utilisateurs non techniques
- Tests d’indicateurs : fournisseurs sans produits, nettoyage de données
- Optimisations techniques (index, typage, harmonisation)

---

## Mission 3 : Analyse avancée par requêtes SQL

- Calcul de KPI stratégiques : chiffre d’affaires par catégorie/année, produits non commandés, CA hors UE, parité pilotes/partenaires
- Requêtes avancées détaillées dans le rapport

**Exemple de requête :**

```SQL
SELECT Produit.NomProd, SUM(DetailCommande.Quantité) AS QuantiteTotale,
SUM(Categorie.CoefMarge * Produit.CoutAchat * DetailCommande.Quantité * (1-DetailCommande.Remise)) AS BeneficeTotal
FROM Categorie
INNER JOIN Produit ON Categorie.CodeCateg = Produit.CodeCateg
INNER JOIN DetailCommande ON Produit.RefProd = DetailCommande.RefProd
GROUP BY Produit.NomProd
ORDER BY QuantiteTotale DESC;
```

---

## Bilan et recommandations

- **Points forts :** modèle relationnel cohérent, segments à fort potentiel, réseau clients efficace
- **Points faibles :** anomalies de saisie, produits non commandés, gouvernance
- **Recommandations :** nettoyage des données, mise en place de monitoring, optimisation du catalogue et des partenariats

---

## Outils utilisés

- **Microsoft Excel** : exploration et analyse initiale
- **Microsoft Access QBE** : interface graphique
- **SQL** : requêtes avancées et automatisation

---

## Arborescence du dépôt

/
├── data/ # Base de données Access et jeux de données
├── web/ # Présentation web en HTML/CSS
├── rapport/ # Rapport PDF final et annexes
├── README.md # Ce document


---

## Liens utiles

- [Sujet complet et consignes](SUJET__Sae104_2025_2026_Mission3.pdf)
- [Synthèse de notre rapport](3_107_108_Mahfoudh_Mokadem_Li_Joaquim.pdf)
- [Guide rendu web & rapport](2025-S1.04-ConsignesRendusRapport-SAE-et-WEB.pdf)

---
