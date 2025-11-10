# Data visualisation

Travaux pratiques pour le cours Data visualisation adressé aux étudiants du Master 2 DS à l'Université d'Angers.

## Séance 1 - GGPLOT2

Utilisation de l'outil GGPLOT2 de RStudio pour concevoir des graphes à partir d'un jeu de données conçu par l'INED.

## Séance 2 - PowerBI

Utilisation de l'outil PowerBI pour concevoir un rapport interactif de jeu de données

Correction RStudio : 

```

# Le code suivant, qui crée un dataframe et supprime les lignes dupliquées, est toujours exécuté et sert de préambule à votre script : 

# dataset <- data.frame(TRANSPORTS1)
# dataset <- unique(dataset)

# Collez ou tapez votre code de script ici :

# Charger ggplot2
library(ggplot2)

# Vérifier que le dataset existe
if(!exists("dataset")) stop("Glisse les champs dans le visuel R")
if(!("TRANSPORTS1" %in% colnames(dataset))) stop("Colonne 'TRANSPORTS1' introuvable")

# Supprimer les doublons
dataset_unique <- unique(dataset)

# Compter les occurrences par chambre
occ <- as.data.frame(table(dataset_unique$TRANSPORTS1))
colnames(occ) <- c("TRANSPORTS1", "Occurrences")  # renommer les colonnes

# Créer le graphique à barres avec valeurs au-dessus
ggplot(occ, aes(x = TRANSPORTS1, y = Occurrences)) +
  geom_col(fill = "skyblue") +  # barres
  geom_text(aes(label = Occurrences), vjust = -0.5, size = 3) +  # valeurs au-dessus
  labs(
    title = "Occurrences de chaque valeur",
    x = "TRANSPORTS1",
    y = "Nombre d'occurrences"
  ) +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))  # rotation labels X
```