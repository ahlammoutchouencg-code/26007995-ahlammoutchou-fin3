# Fiche du sujet F3 : Prévision de l'inflation

> Fiche reconstituée à partir de l'énoncé du CC (annexe sur les sujets) et du projet réalisé. La fiche officielle détaillée est dans `projets_finance_science_donnees.md` (fichier fourni par l'enseignant) ; si tu l'as, remplace ce contenu par la section F3 de ce fichier.

| Rubrique | Contenu |
| --- | --- |
| Identifiant et titre | F3 : Prévision de l'inflation |
| Tâche | Régression sur séries mensuelles |
| Algorithmes du support conseillés (annexe A) | 1, 2, 3, 6, 7, 16 |
| Algorithme principal retenu | n°2 : régression Ridge |
| Risque signalé dans l'énoncé | Séries révisées après publication (biais d'anticipation) |

## Question
Le taux de chômage et le taux directeur de la Fed aident-ils à prévoir l'inflation américaine 12 mois à l'avance, mieux qu'une référence simple ?

## Données
Séries mensuelles FRED : CPIAUCSL (IPC), UNRATE (chômage), FEDFUNDS (taux directeur) ; extension : CPILFESL (IPC hors alimentation et énergie).

## Prétraitement
Inflation sur 12 mois = 100 × (IPC_t / IPC_{t-12} − 1) ; cible = inflation à t+12 ; variables construites avec le passé seulement (retards 3, 6, 12 mois, variations) ; interpolation des mois manquants isolés.

## Modèles
Références : « dernière valeur » et « moyenne historique ». Modèle principal : Ridge standardisé (Pipeline).

## Métriques
RMSE (principale), MAE et R² ; validation croisée temporelle (TimeSeriesSplit).

## Risques
Biais d'anticipation (séries révisées, désaisonnalisation), changements de régime, un seul découpage de test, corrélations trompeuses.
