# F3 : Prévision de l'inflation américaine à 12 mois

**Étudiante :** Ahlam Moutchou | **Code Apogée :** 26007995 | **Groupe :** 3 | **Filière :** S7 FIN

## Problématique
Le taux de chômage et le taux directeur de la Fed aident-ils à prévoir l'inflation américaine 12 mois à l'avance, mieux qu'une prévision qui suppose que l'inflation restera à son niveau actuel ?

**Objectif mesurable :** RMSE de test du Ridge (inflation + chômage + taux directeur) inférieure d'au moins 10 % à celle de la référence « dernière valeur », sur la période de test 2010-2025.

## Résultats principaux
| Modèle | RMSE validation croisée | RMSE test |
| --- | --- | --- |
| Référence (dernière valeur) | 2,03 | 2,04 |
| Ridge, inflation + chômage + taux (modèle principal) | 2,41 | 2,54 |
| Ridge, inflation seule | 2,12 | 1,78 |
| Ridge, inflation + inflation sous-jacente | 2,16 | 1,72 |

- Objectif **non atteint** : le modèle principal est moins bon que la référence de 24,5 % sur le test.
- Ajouter le chômage et le taux directeur à l'inflation passée augmente l'erreur, en validation croisée comme sur le test.
- L'erreur dépend fortement de la période (RMSE 1,54 avant 2020, 4,18 en 2020-2022).

## Données
- Source : FRED (Réserve fédérale de Saint-Louis), https://fred.stlouisfed.org
- Séries mensuelles : CPIAUCSL, UNRATE, FEDFUNDS, CPILFESL. Date d'extraction : 17/11/2026.
- Échantillon utilisable : 802 observations (janvier 1959 à octobre 2025). Licence : voir https://fred.stlouisfed.org/legal#fred-terms-faq

## Installation et exécution
```bash
pip install -r requirements.txt
```
Ouvrir `notebooks/projet_F3.ipynb` (Jupyter ou Google Colab), puis « Redémarrer et tout exécuter ». Les données brutes sont lues dans `data/raw/` (téléchargées depuis FRED si absentes). Graine aléatoire : 42.

## Structure du dépôt
```
README.md, requirements.txt, DECLARATION_IA.md, .gitignore
data/raw/          données brutes (CSV FRED)
data/processed/    données préparées
docs/              fiche du sujet
notebooks/         projet_F3.ipynb
figures/           graphiques
rapport/           rapport.pdf
presentation/      6 diapositives (PDF et PPTX)
```

## Références
FRED (CPIAUCSL, UNRATE, FEDFUNDS, CPILFESL) ; documentation scikit-learn et pandas ; support du cours `Tp_ML.ipynb`.
