# RGPD santé + AI Act — Mini-cours

> Brief associé : M7-B1
> Durée de lecture : ~30 min
> Pré-requis : notions RGPD de base (M2)

## Pourquoi cette techno ?

En santé, la conformité n'est pas optionnelle : les données sont **sensibles**
(RGPD art. 9) et un système d'IA qui influence les soins tombe très probablement
sous le régime **« haut risque »** de l'AI Act. Savoir **nommer les articles et
les obligations** transforme un audit vague en rapport défendable devant un DPO.
Vous n'êtes pas juriste — vous **signalez les risques** et pointez les obligations
probables, sans rédiger d'AIPD.

## Concepts clés

- **RGPD art. 9** : les données de santé sont une **catégorie particulière** →
  traitement interdit par défaut, sauf base légale renforcée (consentement,
  mission de santé publique). À **vérifier**, pas à présumer.
- **Minimisation (art. 5)** : ne collecter/utiliser que le nécessaire. Une
  variable sensible inutile (ex. `sexe` qui crée du biais) doit être retirée.
- **Décision automatisée (art. 22)** : une personne a le droit de ne pas faire
  l'objet d'une décision **uniquement automatisée** → supervision humaine, recours.
- **AI Act — classification** : Annexe III liste les usages « haut risque »
  (dont la santé). Un système classé « haut risque » a des **obligations**.
- **3 obligations clés** : **transparence** (informer sur la logique),
  **traçabilité/journalisation** (logs des décisions), **supervision humaine**
  (HITL). Si elles manquent → non-conformité.

## Exemple minimal qui tourne

```markdown
- Art. 9 RGPD : données de santé → base légale à prouver.
- Art. 22 : la DMS prédite arbitre-t-elle sans revue humaine ? → risque.
- AI Act Annexe III : santé = haut risque → transparence + traçabilité + HITL.
```

## Exercice guidé

Pour le DMS predictor MediVox :
1. Liste 2 obligations RGPD probablement non satisfaites (traçabilité, conservation…).
2. Cite les 3 obligations AI Act « haut risque » avec une référence approximative.
3. Le système relève-t-il de l'art. 22 (décision automatisée) ? Justifie.

## Pièges fréquents

| Piège | Conséquence |
|---|---|
| Présumer la base légale RGPD | On valide à tort une non-conformité |
| Rédiger une AIPD complète | Hors mandat d'audit |
| Ignorer l'art. 22 | On rate le risque « décision automatisée » |
| Citer l'AI Act sans classification | Obligations hors-sol |
| Confondre RGPD et AI Act | Deux cadres distincts (données vs système IA) |

| Symptôme | Cause probable |
|---|---|
| Marc (DPO) conteste le rapport | obligations non rattachées à un article |
| « Le système est conforme » trop vite | base légale art. 9 non vérifiée |
| Pas de mention HITL | art. 22 / AI Act supervision oubliés |

## Pour aller plus loin

- CNIL — IA et RGPD : https://www.cnil.fr/fr/intelligence-artificielle/ia-comment-etre-en-conformite-avec-le-rgpd
- AI Act — Annexe III : https://artificialintelligenceact.eu/annex/3/

## Vérification (checklist apprenant)

- [ ] Je cite l'art. 9 (santé) et la base légale à vérifier.
- [ ] Je liste les 3 obligations AI Act « haut risque ».
- [ ] Je traite l'art. 22 (décision automatisée + recours).
- [ ] Je signale les risques **sans** rédiger d'AIPD.
- [ ] Mes références d'articles sont présentes (même approximatives).

> 💡 **Récap** : en santé, RGPD **art. 9** (données sensibles, base légale à
> prouver) + **art. 22** (décision automatisée, recours humain) + AI Act **« haut
> risque »** (Annexe III) ⇒ 3 obligations : **transparence, traçabilité, supervision
> humaine**. L'auditeur **signale** ces risques avec une référence d'article ; il ne
> rédige pas l'AIPD (hors mandat).

*Réflexe : RGPD encadre les **données**, l'AI Act encadre le **système d'IA** — deux cadres complémentaires, pas interchangeables.*
