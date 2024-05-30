# Credit-Risk-Model-Stability

Le but de ce projet (qui est une compétition KAGGLE) est de prédire quels clients sont les plus susceptibles de ne pas rembourser leurs prêts. On devra privilégier les solutions stables dans le temps.
Ce projet pourra par exemple offrir aux prestataires de crédit à la consommation un moyen plus fiable et plus durable d’évaluer le risque de défaut d’un client potentiel.

Actuellement, les prestataires de crédit à la consommation utilisent diverses méthodes statistiques et d'apprentissage automatique pour prédire le risque de prêt. Ces modèles sont généralement appelés tableaux de bord. Dans le monde réel, les comportements des clients changent constamment, et donc chaque tableau de bord doit donc être mis à jour régulièrement. La stabilité du tableau de bord à l'avenir est essentielle, car une baisse soudaine des performances signifie que les prêts seront en moyenne accordés à des clients moins bons. Le cœur du problème est que les prêteurs ne sont pas en mesure de détecter les problèmes potentiels avant que les premières dates d’échéance de ces prêts ne soient observables. Compte tenu du temps nécessaire pour réélaborer, valider et mettre en œuvre la carte de pointage, la stabilité est hautement souhaitable. Il existe un compromis entre la stabilité du modèle et ses performances, et un équilibre doit être atteint avant le déploiement.

Pour évaluer notre modèle, on utilisera une métrique de stabilité Gini. Un score Gini est calculé pour les prédictions correspondant à chaque WEEK_NUM: **Gini=2×AUC−1Gini=2×AUC−1**.\
Une régression linéaire **a*x+b**, est ajustée à travers les scores Gini hebdomadaires, et un falling_rate est calculé comme min⁡(0,a), et cela est utilisé pour pénaliser les modèles qui perdent en capacité prédictive.

Enfin, la variabilité des prédictions est calculée en prenant l'écart-type des résidus de la régression linéaire ci-dessus, en appliquant une pénalité à la variabilité du modèle.

La métrique finale est calculée comme : **stability metric = mean(gini)+88.0⋅min⁡(0,a)−0.5⋅std(residuals)stability**
