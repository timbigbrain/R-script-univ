### TP 1
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

extraction1 <- subset(dfManga, Score > 9)
nrow(extraction1)

extraction2 <- subset(dfManga, Vote >= 200000)
nrow(extraction2)

extraction3 <- subset(dfManga, Vote > 200000 & Score > 8)
nrow(extraction3)


extraction4 <- subset(dfManga, Score >= 7 & Score <= 8)
nrow(extraction4)

effectifRating <- table(dfAnime$Rating)
print(effectifRating)

length(effectifRating)

prop.table(effectifRating)
extraction2 <- subset(dfAnime, Rating == "R - 17+ (violence & profanity)")
nrow(extraction2)

extraction3 <- subset(dfAnime, Rating == "R - 17+ (violence & profanity)" & Score >= 8)
nrow(extraction3)

extraction4 <- subset(dfAnime, Rating != "R - 17+ (violence & profanity)")
nrow(extraction4)

extraction5 <- subset(dfAnime, Rating %in% c("PG - Children","G - All Ages"))
nrow(extraction5)

extraction6 <- subset(dfAnime, !Rating %in% c("PG - Children","G - All Ages"))
nrow(extraction6)

extraction7 <- subset(dfAnime, Score >= 9 | Vote > 400000)
nrow(extraction7)

```

### TD 2
## Exercice 1
```r
setwd("L:/BUT/SD/Promo 2025/tjacon/datasets")

bodies_karts <- read.csv("bodies_karts.csv", header = TRUE, sep = ";", dec = ",")
tires <- read.csv("tires.csv", header = TRUE, sep = "\t", dec = ",")
gliders <- read.csv("gliders.csv", header = TRUE, sep = "|", dec = ".")
drivers <- read.csv("drivers.csv", header = TRUE, sep = ";", dec = ",")


getwd()
```
## Exercice 2
```r
dim(bodies_karts)
dim(tires)
dim(gliders)
dim(drivers)

summary(bodies_karts)
summary(tires)
summary(gliders)
summary(drivers)


plot(x = drivers$Weight, y = drivers$Acceleration, main = "Drivers : Weight/Acceleration")

cor(x = drivers$Weight, y = drivers$Acceleration)

covxy = cov(x = drivers$Weight, y = drivers$Acceleration)
sdx = sd(drivers$Weight)
sdy = sd(drivers$Acceleration)

print(covxy / (sdx*sdy))

coefCorr = cor(x = drivers$Weight,
               y = drivers$Acceleration)
coefDeter = coefCorr^2
print(coefDeter)

matriceCor = cor(drivers[ , - 1])
matriceCor = round(matriceCor , 2)
View(matriceCor)
#Les résultats se rapproche tous de 1 ou -1 donc les variables sont fortement corrélées

install.packages("corrplot")

library(corrplot) 
corrplot(matriceCor, method="circle")

matriceCor = round(cor(tires[ , - 1]),1)
corrplot(matriceCor, method="color",  
         type="upper", order="hclust", 
         addCoef.col = "black", # Ajout du coefficient de corrélation
         tl.col="black", tl.srt=45, #Rotation des étiquettes de textes
         # Cacher les coefficients de corrélation sur la diagonale
         diag=FALSE 
)


matriceCor = round(cor(bodies_karts[ , - 1]),1)
corrplot(matriceCor, method="color",  
         type="upper", order="hclust", 
         addCoef.col = "black", # Ajout du coefficient de corrélation
         tl.col="black", tl.srt=45, #Rotation des étiquettes de textes
         # Cacher les coefficients de corrélation sur la diagonale
         diag=FALSE 
)

matriceCor = round(cor(gliders[ , - 1]),1)
corrplot(matriceCor, method="color",  
         type="upper", order="hclust", 
         addCoef.col = "black", # Ajout du coefficient de corrélation
         tl.col="black", tl.srt=45, #Rotation des étiquettes de textes
         # Cacher les coefficients de corrélation sur la diagonale
         diag=FALSE 
)
```
### Exercice 3
```r
resultat = drivers[ , c("Driver" , "Weight")]
View(resultat)

resultat = drivers[ 1:10 , c("Driver" , "Acceleration")]
View(resultat)

resultat = drivers[ , -c(5,7,9)]
View(resultat)

resultat = drivers[ , -c("Weight","Acceleration")] 
resultat = drivers[ , -c(2,3)]

resultat = drivers[ , c("Driver", "Acceleration", "Weight")]
View(resultat)

resultat = drivers[ c(3,12,32) , ]
View(resultat)
resultat = drivers[ c(32,3,12) , ]
view(resultat)

rang = order(drivers$Acceleration, decreasing = TRUE)
resultat = drivers[ rang  , c("Driver", "Acceleration") ]
View(resultat)

rang = order(drivers$Acceleration, drivers$Weight, decreasing = c(TRUE,FALSE))
resultat = drivers[ rang  , c("Driver", "Acceleration","Weight") ]
View(resultat)
```
### Exercice 4
```r
help(subset)
topDriver = subset(x = drivers,
                   subset = Acceleration == max(Acceleration), 
                   select = c("Driver","Acceleration"))
```
### TP 2
## Exercice 1
```r
df<-read.csv("fao.csv", sep=";", dec=",", header = TRUE)
nrow(df)
summary(df)
```
## Exercice 2
```r
mean(df$Dispo_alim, na.rm=TRUE)
sum(df$Population, na.rm=TRUE)
sd(df$Export_viande, na.rm=TRUE)
sd(df$Import_viande, na.rm=TRUE)
median(df$Prod_viande, na.rm=TRUE)
quantile(df$Dispo_alim)
quantile(df$Import_viande, seq(0,1,0.01))
```
## Exercice 3
```r
rang = order(df$Population)
resultat = head(df[ rang , ], n = 5)
View(resultat)
rang = order(df$Population, decreasing = TRUE)
resultat = head(df[ rang , ], n = 5)
View(resultat)
rang = order(df$Prod_viande, decreasing = TRUE)
resultat = head(df[ rang , ], n = 5)
View(resultat)
rang = order(df$Import_viande, decreasing = TRUE)
resultat = head(df[ rang , ], n = 5)
View(resultat)
resultat = subset(df, Dispo_alim>=2300)
View(resultat)
resultat = subset(df, Dispo_alim > 3500  & Import_viande > 1000)
View(resultat)
resultat = subset(df, Nom %in% c("France","Belgique"))
View(resultat)
```
## Exercice 4
```r
df$Part_export<-df$Export_viande/df$Prod_viande
df$Dispo_alim_pays<-df$Dispo_alim*df$Population
write.table(x = df, file = "ExportTp2.csv")
dispo_alim_mondiale = sum(df$Dispo_alim_pays, na.rm=TRUE)
dispo_alim_mondiale
dispo_alim_mondiale/2300
```
## Exercice 5
```r
plot(x = df$Prod_viande,
     y = df$Export_viande, 
     main = "Pays : Prod_viande / Export_viande")

cor(x = df$Prod_viande,
    y = df$Export_viande)

matriceCor = cor(df[ , - 1] , use = "complete.obs")
matriceCor = round(matriceCor , 2)
View(matriceCor)
#commande à executer qu'une seule fois
install.packages("corrplot")
library(corrplot) #je charge mon package pour pouvoir utiliser ses fonctionalités
corrplot(matriceCor, method="circle")
```
### TD 3
## Exercice 1
```r
pokemon <- readxl::read_excel(
  path = "C:/Users/tjacon/Downloads/pokemon.xlsx",
  sheet = "pokemon")

dim(pokemon)
ncol(pokemon)
nrow(pokemon)

summary(pokemon)

pokemon$is_legendary <-as.factor(pokemon$is_legendary)
pokemon$generation <-as.factor(pokemon$generation)
pokemon$type <-as.factor(pokemon$type)

summary(pokemon)
```
## Exercice 2
```r
med = median(pokemon$attack)
pokemon$attack_group = ifelse(pokemon$attack >= med, "attack+","attack-")
pokemon$attack_group <-as.factor(pokemon$attack_group)
summary(pokemon$attack_group)

pokemon$water_fire = ifelse(pokemon$type %in% c("water","fire"), "yes","no")
pokemon$water_fire <-as.factor(pokemon$water_fire)
summary(pokemon$water_fire)


q3_attack = quantile(pokemon$attack, probs = 0.75)
q3_defense = quantile(pokemon$defense, probs = 0.75)
q3_speed = quantile(pokemon$speed, probs = 0.75)
pokemon$best = ifelse(pokemon$attack > q3_attack &
                        pokemon$defense > q3_defense &
                        pokemon$speed > q3_speed , "yes","no")
pokemon$best <-as.factor(pokemon$best)
summary(pokemon$best)

requette = subset(pokemon,is.na(weight_kg))
View(requette)

med_weight_kg = median(pokemon$weight_kg, na.rm = TRUE)
pokemon$weight_kgNa = ifelse(is.na(pokemon$weight_kg) , 
                             med_weight_kg ,
                             pokemon$weight_kg)

med_height_m = median(pokemon$height_m, na.rm = TRUE)
pokemon$height_mNA = ifelse(is.na(pokemon$height_m) , 
                            med_height_m ,
                            pokemon$height_m)

pokemon$weight_group = cut(pokemon$weight_kg,
                           breaks = 3,
                           labels = c("léger","moyen","lourd"))

pokemon$height_m_group = cut(pokemon$height_m,
                             breaks = c(0,1,2,3,
                                        max(pokemon$height_m,
                                            na.rm = TRUE)))

pokemon$defense_group = cut(pokemon$defense,
                            breaks = quantile(pokemon$defense,
                                              na.rm = TRUE),
                            include.lowest = TRUE)
summary(pokemon$defense_group)

med = median(pokemon$attack)
pokemon$attack_group = ifelse(pokemon$attack >= med, "attack+","attack-")
pokemon$attack_group <-as.factor(pokemon$attack_group)
summary(pokemon$attack_group)

pokemon$water_fire = ifelse(pokemon$type %in% c("water","fire"), "yes","no")
pokemon$water_fire <-as.factor(pokemon$water_fire)
summary(pokemon$water_fire)


q3_attack = quantile(pokemon$attack, probs = 0.75)
q3_defense = quantile(pokemon$defense, probs = 0.75)
q3_speed = quantile(pokemon$speed, probs = 0.75)
pokemon$best = ifelse(pokemon$attack > q3_attack &
                        pokemon$defense > q3_defense &
                        pokemon$speed > q3_speed , "yes","no")
pokemon$best <-as.factor(pokemon$best)
summary(pokemon$best)

requette = subset(pokemon,is.na(weight_kg))
View(requette)

med_weight_kg = median(pokemon$weight_kg, na.rm = TRUE)
pokemon$weight_kgNa = ifelse(is.na(pokemon$weight_kg) , 
                             med_weight_kg ,
                             pokemon$weight_kg)

med_height_m = median(pokemon$height_m, na.rm = TRUE)
pokemon$height_mNA = ifelse(is.na(pokemon$height_m) , 
                            med_height_m ,
                            pokemon$height_m)

pokemon$weight_group = cut(pokemon$weight_kg,
                           breaks = 3,
                           labels = c("léger","moyen","lourd"))

pokemon$height_m_group = cut(pokemon$height_m,
                             breaks = c(0,1,2,3,
                                        max(pokemon$height_m,
                                            na.rm = TRUE)))

pokemon$defense_group = cut(pokemon$defense,
                            breaks = quantile(pokemon$defense,
                                              na.rm = TRUE),
                            include.lowest = TRUE)
summary(pokemon$defense_group)
```
## Exercice 3
```r
aggregate(x = attack ~ type, 
          data = pokemon,
          FUN = function(x) mean(x))
aggregate(x = attack ~ generation + type,
          data = pokemon, 
          FUN = function(x) median(x))
aggregate(x = pokedex_number ~ type,
          data = pokemon,
          FUN = function(x) length(x))
aggregate(speed ~ generation + type,
          data = pokemon, 
          FUN = function(x) c(moy = mean(x),
                              med = median(x),
                              eff = length(x) ) )
```
### TP 1
## Exercice 1
```r
salaire_net_cadre = function(salaire_brut){
  result = salaire_brut*0.75
  return(result)
}

salaire_net_cadre(2000)


salaire_net_cadre = function(salaire_brut=2500){
  result = salaire_brut*0.75
  return(result)}

salaire_net_cadre()

salaire_net_cadre = function(salaire_brut = 2500, temps_tr = 1){
  result = salaire_brut*0.75
  return(result)}

salaire_net_cadre()

salaire_net_cadre = function(salaire_brut = 2500, temps_travail = 1){
  if (is.numeric(salaire_brut)){   result = salaire_brut*0.75
  return(result)}
  return("Erreur :  le salaire brut doit être une valeur numérique")}

salaire_net_cadre(salaire_brut = "2000€")
salaire_net_cadre(salaire_brut = 2000)

salaire_net_cadre = function(salaire_brut = 2500,temps_travail = 1) {
  
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }
  
  if (!is.numeric(temps_travail)) {
    return("Erreur :  le temps de travail doit doit être une valeur numérique")
  }
  
  if ( (temps_travail > 1) | (temps_travail < 0)) {
    return("Erreur :  le temps de travail doit être une valeur numérique entre 0 et 1")
  }
  
  salaire_net_avant_impot = salaire_brut * 0.75 * temps_travail
  return(salaire_net_avant_impot) 
}
#Test de la fonction
salaire_net_cadre(salaire_brut = 2000, temps_travail = "100%")
salaire_net_cadre(salaire_brut = 2000, temps_travail = 0.8)
salaire_net_cadre(salaire_brut = 2000, temps_travail = 100)


salaire_net = function(salaire_brut, temps_travail, statut){
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }
  
  if (!is.numeric(temps_travail)) {
    return("Erreur :  le temps de travail doit doit être une valeur numérique")
  }
  
  if ( (temps_travail > 1) | (temps_travail < 0)) {
    return("Erreur :  le temps de travail doit être une valeur numérique entre 0 et 1")
  }
  
  if (!statut %in% c("cadre","non cadre")) {
    return("Erreur :  le statut doit être cadre ou non cadre")
  }
  if (statut == "cadre"){
    result = salaire_brut*0.78
  } 
  else if (statut == "non cadre"){
  result = salaire_brut*0.75}
return(result)}

salaire_net(salaire_brut = 2000, temps_travail = 1,   statut = "cadre")
salaire_net(salaire_brut = 2000, temps_travail = 1, statut = "non cadre")
salaire_net(salaire_brut = 2000, temps_travail = 1, statut = "technicien")

salaire_net = function(salaire_brut = 2500,temps_travail = 1, statut) {
  
  if (!is.numeric(salaire_brut)) {
    return("Erreur :  le salaire brut doit être une valeur numérique")
  }
  
  if (!is.numeric(temps_travail)) {
    return("Erreur :  le temps de travail doit doit être une valeur numérique")
  }
  
  if ( (temps_travail > 1) | (temps_travail < 0)) {
    return("Erreur :  le temps de travail doit être une valeur numérique entre 0 et 1")
  }
  
  if (!statut %in% c("cadre","non cadre")) {
    return("Erreur :  le statut doit être cadre ou non cadre")
  }
  
  if (statut == "cadre") {
    salaire_net_avant_impot = salaire_brut * temps_travail * 0.75
  } else {
    salaire_net_avant_impot = salaire_brut * temps_travail * 0.78
  }
  
  if (salaire_net_avant_impot <= 1591) {
    salaire_net_apres_impot <- salaire_net_avant_impot
  } else if (salaire_net_avant_impot <= 2006) {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.029)
  } else if (salaire_net_avant_impot <= 3476) {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.099)
  } else if (salaire_net_avant_impot <= 8557) {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.20)
  } else {
    salaire_net_apres_impot <- salaire_net_avant_impot * (1 - 0.43)
  }
  
  return(salaire_net_apres_impot) 
}

shifumi <- function() {
 
  choix_utilisateur <- readline(prompt = "Choisissez entre pierre, papier ou ciseaux : ")
  
 
  if (choix_utilisateur %in% c("pierre", "papier", "ciseaux")) {
    
    choix_ordi <- sample(c("pierre", "papier", "ciseaux"), 1)
    
    
    cat("Votre choix :", choix_utilisateur, "\n")
    cat("Choix de l'ordinateur :", choix_ordi, "\n")
    
   
    if (choix_utilisateur == choix_ordi) {
      return("Égalité !")
    } else if ((choix_utilisateur == "pierre" & choix_ordi == "ciseaux") |
               (choix_utilisateur == "papier" & choix_ordi == "pierre") |
               (choix_utilisateur == "ciseaux" & choix_ordi == "papier")) {
      return("Vous avez gagné !")
    } else {
      return("L'ordinateur a gagné !")
    }
  } else {
    return("Valeur invalide. Veuillez choisir entre pierre, papier ou ciseaux.")
  }
}

shifumi()

resultat = 0
for (element in c(1,2,3,4,5)) {
  resultat = resultat +  element
  print(paste("le resultat est : ",resultat))
}

element = 1
resultat = 0
while (resultat <= 50) {
  resultat = resultat +  element
  print(paste("le resultat est : ",resultat))
  print(paste("le programme s'est arrêté à la valeur : ", element))
  element = element + 1
}

for (colonne in colnames(iris)) {
  type_colonne = class(iris[ , colonne])
  print(paste("la colonne ", colonne, " est de type : ", type_colonne))
}

indice_colonne <- 1

while (indice_colonne <= ncol(iris)) {
  nom_colonne <- colnames(iris)[indice_colonne]
  
  type_colonne <- class(iris[, nom_colonne])
  
  print(paste("la colonne ", nom_colonne, " est de type : ", type_colonne))
  
  indice_colonne <- indice_colonne + 1
}

for (i in 1:5) {
  
  nombre <- readline(prompt = "Entrez le nombre :")
  nombre <- as.numeric(nombre)
  
  carre <- nombre^2
  
  print(paste("Le carré de", nombre, "est", carre))
}
```
