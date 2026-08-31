# Procédure d'audit IA — template 7 sections (MediVox)

> Procédure **fournie** : remplissez chaque section. Un audit **outillé**, pas
> improvisé. Périmètre = observer/documenter/hiérarchiser (≠ corriger, ≠ AIPD).

## 1. Périmètre et hors-périmètre
_Ce qui est audité (modèle, code, dataset) ; ce qui est exclu (pen-test, AIPD,
refonte). Les 2 lectorats du rapport (technique / DPO)._

## 2. Audit éthique
_Variables sensibles (directes/indirectes) ; **disparate impact chiffré** sur ≥ 1
variable ; RGPD santé (art. 9, minimisation, conservation) ; AI Act (classification
risque + 3 obligations probables) ; décision automatisée (art. 22)._

## 3. Audit technique
_Architecture (modularité, couplage) ; sécurité (secrets, validation, transport) ;
scalabilité ; **points de rupture** (SPOF)._

## 4. Audit ressources
_Mesures **psutil** (temps train/inférence, RSS, taille modèle) ; comparaison à
**≤ 2 alternatives** ; lecture sobriété (chiffrée, honnête)._

## 5. Tableau d'indicateurs consolidé
_12-18 lignes : indicateur / sévérité (🔴🟠🟡) / conséquence client. Hiérarchisé,
pas tout au même niveau._

## 6. Synthèse exécutive
_½ page lisible en 5 min par un décideur non-ML (le « plus grave » d'abord)._

## 7. Questions ouvertes
_Ce qu'il faut clarifier avec le client avant toute évolution._
