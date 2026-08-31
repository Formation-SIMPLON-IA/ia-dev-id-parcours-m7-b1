# Disparate impact (en audit) — Mini-cours

> Brief associé : M7-B1
> Durée de lecture : ~20 min
> Pré-requis : pandas, notion de variable sensible (revu de M2-B2)

## Pourquoi cette techno ?

En audit éthique, « il y a peut-être un biais » ne suffit pas : il faut le
**mesurer**. Le **disparate impact** (DI) quantifie si un modèle traite des
groupes protégés à des taux comparables. C'est l'indicateur le plus simple et le
plus reconnu (règle des **4/5**), directement opposable devant un DPO ou un
régulateur. Ici on l'applique à un modèle **déjà en prod** (audit), pas à un
dataset à nettoyer (M2).

## Concepts clés

- **DI = taux(groupe défavorisé) / taux(groupe favorisé)** sur l'issue
  (ici : prédiction « séjour prolongé »).
- **Règle des 4/5** : DI < **0.80** signale un biais défavorable au groupe.
- **Sur le modèle, pas que le dataset** : on calcule le DI sur les **prédictions**
  du modèle audité → révèle s'il **amplifie** un biais des étiquettes.
- **Variable sensible en feature** : si le modèle utilise `sexe` directement,
  le biais est **direct** (aggravant majeur).
- **Croiser** : DI par sexe **et** par tranche d'âge ; distinguer effet
  légitime (médical) d'un proxy discriminant.

## Exemple minimal qui tourne

```python
import pandas as pd, joblib
df = pd.read_csv("data/dms_dataset.csv")
model = joblib.load("legacy/dms_predictor_v1.joblib")
X = df[["age","nb_comorbidites","imc"]].assign(sexe_bin=(df["sexe"]=="M").astype(int))
df["pred"] = model.predict(X)
rate = df.groupby("sexe")["pred"].mean()
print("DI F/M =", round(rate["F"]/rate["M"], 3))   # < 0.80 → biais
```

## Exercice guidé

Sur le DMS predictor :
1. Calcule le DI F/M **sur les prédictions** du modèle.
2. Compare-le au DI des **étiquettes** (`sejour_prolonge`). Le modèle amplifie-t-il ?
3. Calcule le taux de prédiction par tranche d'âge. Effet légitime ou suspect ?

## Pièges fréquents

| Piège | Conséquence |
|---|---|
| DI calculé sur le dataset au lieu du modèle | On rate l'amplification par le modèle |
| Conclure biais sur l'âge sans contexte médical | Faux positif (effet légitime) |
| Ignorer que `sexe` est une feature | On manque l'aggravant « discrimination directe » |
| Seuil flou | Utiliser la règle des 4/5 (0.80) comme référence |

| Symptôme | Cause probable |
|---|---|
| DI proche de 1 sur le dataset mais < 0.8 sur le modèle | le modèle amplifie le biais |
| DI très bas sur l'âge | possible effet médical légitime à documenter |

## Pour aller plus loin

- EEOC — règle des 4/5 : https://www.eeoc.gov/laws/guidance/employment-tests-and-selection-procedures
- scikit-learn — metrics : https://scikit-learn.org/stable/modules/model_evaluation.html

## Vérification (checklist apprenant)

- [ ] Je calcule le DI **sur les prédictions** du modèle.
- [ ] Je le compare au DI des étiquettes (amplification ?).
- [ ] J'utilise la règle des 4/5 (0.80).
- [ ] Je distingue effet légitime (âge médical) d'un biais.
- [ ] Je signale si une variable sensible est utilisée en feature.

> 💡 **Récap** : on calcule le DI **sur les prédictions du modèle** (pas seulement
> sur le dataset) pour révéler une **amplification** du biais. Règle des **4/5**
> (< 0.80 = biais). Aggravant majeur si une variable sensible (sexe) est utilisée
> **en feature**. Distinguer un effet médical légitime (âge) d'un proxy discriminant.

*Réflexe : un DI proche de 1 sur le dataset mais bas sur le modèle = le modèle **crée** le biais — souvent parce qu'il utilise la variable sensible.*

*Et toujours : le DI est un **signal**, pas une preuve juridique — il déclenche l'investigation, il ne la remplace pas.*
