###TP 1
```r
class(iris)
View(iris)
nrow(iris)
ncol(iris)
colnames(iris)
summary(iris)

iris[, c("Sepal.Length", "Species")]
iris[c(100, 103, 105), ]
iris[50:100, ]

mean(iris$Sepal.Length)
median(iris$Sepal.Length)
sd(iris$Petal.Length)
quantile(iris$Petal.Width, probs = seq(from = 0.1, to = 0.9, by = 0.1))

dfManga <- read.csv("C:/Users/tjacon/Downloads/manga.csv", header = TRUE, sep = ",", dec = ".")
dfAnime <- read.csv("C:/Users/tjacon/Downloads/anime.csv", header = TRUE, sep = ",", dec = ".")

View(dfManga)
View(dfAnime)

dim(dfManga)
dim(dfAnime)

mean(dfManga$Score)
mean(dfAnime$Score)
sum(dfManga$Vote)
sum(dfAnime$Vote)
sd(dfManga$Score)
sd(dfAnime$Score)

quantile(dfManga$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))
quantile(dfAnime$Score, probs = seq(from = 0.1, to = 0.9, by = 0.1))
```
