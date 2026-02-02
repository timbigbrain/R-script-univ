# R-script-univ
## TP 1
### 1
'iris
class(iris) 'la classe d Iris'
View(iris) 'visuamiser iris en tableau'
nrow(iris) 'nb lignes'
ncol(iris)'nb colonnes'
colnames(iris) 'Afficher le nom des colonnes'
summary(iris) 'Afficher un résumé du dataframe'
iris[ , c("Sepal.Length","Species")] 'Afficher uniquement les colonnes précisées'
iris[ c(100,103,105) , ] 'Afficher uniquement la ligne 100,103 et 105.'
iris[c(50:100),]'Afficher uniquement les lignes 50 à 100.'
mean(iris$Sepal.Length) 'Calculer la moyenne de la variable'
median(iris$Sepal.Length) 'Calculer la médiane de la variable'
sd(iris$Petal.Length) 'Calculer l écart-type de la variable'
quantile(iris$Petal.Width, probs = seq(from = 0.1, to = 0.9, by =0.1)) 'Calculer les déciles de la variable '
### 2
dfManga <- read.csv("C:/Users/tjacon/Downloads/manga.csv", header = TRUE, sep = ",", dec = ".")
dfAnime <- read.csv("C:/Users/tjacon/Downloads/anime.csv", header = TRUE, sep = ",", dec = ".")
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
quantile(dfAnime$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))'
