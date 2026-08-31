# Procédure d'audit IA — Mini-cours

> Brief associé : M7-B1
> Durée de lecture : ~25 min
> Pré-requis : avoir un système IA à observer

## Pourquoi cette techno ?

Auditer « à l'instinct » donne un rapport incomplet et non reproductible. Une
**procédure formalisée** garantit qu'on couvre les bons axes (éthique, technique,
ressources), qu'on **chiffre** au lieu de juger, et qu'on **hiérarchise** les
risques. C'est ce que demande un client régulé (santé, finance) face à l'AI Act :
un audit **outillé**, défendable, pas une opinion.

Ce n'est ni un pen-test, ni une AIPD juridique complète : l'audit **observe,
documente et priorise** — il ne corrige pas et ne tranche pas l'architecture
cible (ça, c'est la phase d'évolution suivante).

## Concepts clés

- **Périmètre / hors-périmètre** : déclarer explicitement ce qu'on audite (modèle,
  code, dataset) et ce qu'on exclut (AIPD, pen-test, refonte). Cadre les attentes.
- **3 volets** : éthique (biais, RGPD, AI Act), technique (archi, sécurité,
  scalabilité), ressources (psutil, sobriété).
- **Chiffrer, pas juger** : « DI F/M = 0.29 », « 207 Mo RSS » — pas « ça
  consomme beaucoup ».
- **Hiérarchiser** : sévérité 🔴/🟠/🟡 + conséquence client. Tout n'est pas au
  même niveau.
- **2 lectorats** : le rapport sert un public technique ET un DPO — un seul
  document, deux grilles de lecture.
- **Questionner** : un bon audit liste ce qu'il ne sait pas encore (questions au
  client).

## Exemple minimal qui tourne

```markdown
## 1. Périmètre
Audité : modèle DMS, code legacy/, dataset. Exclu : AIPD, pen-test, refonte.

## 5. Tableau consolidé
| Indicateur | Sévérité | Conséquence client |
|---|---|---|
| sexe utilisé en feature | 🔴 | discrimination directe indéfendable |
```

## Exercice guidé

À partir de `procedure_audit.md` (fourni) :
1. Remplis la section **Périmètre** pour le cas MediVox.
2. Note 3 observations évidentes en lisant `legacy/` (sans le modifier).
3. Classe-les en 🔴/🟠/🟡.

## Pièges fréquents

| Piège | Conséquence |
|---|---|
| Audit non chiffré | Rapport contestable, non actionnable |
| Tout en 🔴 | Plus de hiérarchie, le client ne sait pas par où commencer |
| Confondre audit et AIPD | Hors mandat, perte de temps |
| Proposer la solution | C'est la phase suivante (M7-B2), pas l'audit |
| Oublier le périmètre | Le client conteste le scope |

| Symptôme | Cause probable |
|---|---|
| Le client demande « donc on fait quoi ? » | l'audit a sur-promis (doit hiérarchiser, pas résoudre) |
| Rapport illisible | un seul jargon pour 2 publics |
| Risques tous égaux | pas de sévérité différenciée |

## Pour aller plus loin

- AI Act — obligations « haut risque » : https://artificialintelligenceact.eu/the-act/
- Model Cards (Mitchell) : https://arxiv.org/abs/1810.03993

## Vérification (checklist apprenant)

- [ ] J'ai déclaré périmètre **et** hors-périmètre.
- [ ] Mes 3 volets sont couverts (éthique / technique / ressources).
- [ ] Mes constats sont **chiffrés**.
- [ ] Mon tableau est **hiérarchisé** (🔴/🟠/🟡).
- [ ] L'audit **questionne** et ne propose pas l'architecture cible.
