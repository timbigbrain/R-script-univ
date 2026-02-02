# R-script-univ

## TP 1

---

## Exercice 1 : Jeu de données iris

### Commandes de base
class(iris)
View(iris)
nrow(iris)
ncol(iris)
colnames(iris)
summary(iris)

### Sélection de données
- `iris[, c("Sepal.Length", "Species")]`
- `iris[c(100, 103, 105), ]`
- `iris[50:100, ]`

### Statistiques descriptives
- `mean(iris$Sepal.Length)`
- `median(iris$Sepal.Length)`
- `sd(iris$Petal.Length)`
- `quantile(iris$Petal.Width, probs = seq(from = 0.1, to = 0.9, by = 0.1))`

---

## Exercice 2 : Manga & Anime

### Importation des données

```r
dfManga <- read.csv("C:/Users/tjacon/Downloads/manga.csv",
                    header = TRUE, sep = ",", dec = ".")

dfAnime <- read.csv("C:/Users/tjacon/Downloads/anime.csv",
                    header = TRUE, sep = ",", dec = ".")
View(dfManga)
View(dfAnime)'Afficher les jeux de données dans des vues pour les visualiser'
dim(dfManga)
dim(dfAnime)'Afficher le nombre de lignes et colonnes avec la fonction'
mean(dfManga$Score)
mean(dfAnime$Score)
sum(dfManga$Vote)
sum(dfAnime$Vote)
sd(dfManga$Score)
sd(dfAnime$Score)
quantile(dfManga$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))
quantile(dfAnime$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))
