# Notes passage à l’échelle

Coût actuel : 300 € pour 1506 images, soit environ 0,20 €/image. Extrapolé linéairement à 4 millions d'images, ce taux nécessiterait environ 850 000 €, largement au-delà des 5000 € disponibles (facteur d'écart d'environ 160).

Cette extrapolation linéaire est cependant trop pessimiste, car le pipeline actuel de 300 € couvre des étapes qui ne se répètent pas à l'identique à grande échelle : l'exploration (PCA, t-SNE) devient inutile une fois la méthode validée, seul l'entraînement semi-supervisé se répète.

Conditions pour rester dans une enveloppe raisonnable à 4M images :
- Passage obligatoire sur GPU (CUDA) pour l'entraînement, en particulier pour la phase 1 sur le jeu faiblement labellisé, dont le temps croît directement avec le volume. Coût de location de puissance de calcul à prévoir en dehors du budget de labellisation de 5000 €.
- Stockage et débit de lecture des données à anticiper, un volume 2600 fois supérieur au dataset actuel change la nature du problème d'infrastructure.
- Qualité du clustering à valider à cette échelle : l'ARI de 0,285 obtenu sur 1506 images n'est pas garanti sur 4 millions de points, une dégradation du clustering affaiblirait directement la qualité des labels faibles produits.

Conclusion : une reproduction à l'identique du pipeline actuel n'est pas budgétairement soutenable à cette échelle. Une version allégée (sans phase d'exploration, GPU pour l'entraînement, validation de la qualité du clustering à grande échelle) est nécessaire pour rester crédible dans l'enveloppe donnée.