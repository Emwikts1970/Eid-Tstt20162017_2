---
  title       : Aufgaben
description : Dieses Testat besteht aus einem Kapitel mit insgesamt 11 Aufgaben. Die Aufgaben können unabhängig voneinander gelöst werden. Wir empfehlen Ihnen jedoch die Bearbeitung in der vorgegebenen Reihenfolge. <br> Beachten Sie, dass gelöste Aufgaben abhängig vom Schwierigkeitsgrad mit 100XP, 150XP oder 200XP belohnt werden. Lösungen, die bis 20 Uhr eingereicht sind werden akzeptiert.

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Testatpunkte

Erinnern Sie sich an das letzte Testat: Es waren 1500XP zu erreichen. Angenommen Sie arbeiten als unterbezahlter Hiwi am Lehrstuhl für Ökonometrie und Ihnen liegen Beobachtungen zur erreichten XP (`XP`) sowie investierter Zeit (`Z`) vor. In ihrer Schusseligkeit haben Sie einen zufälligen Teil der Daten unwiederbringlich gelöscht und müssen nun Regressionsanalyse & Inferenzstatistik anhand einer Stichprobe betreiben. Der Zusammenhang wird im Plot-Panel dargestellt.

Sie interessieren sich für das folgende Model:

$$ XP\_i = \beta\_0 + \epsilon\_i  $$

*Die Vektoren `XP` und `Z` sind in Ihrer Arbeitsumgebung verfügbar.*

***=instructions

Berechnen Sie den OLS-Schätzer für $\beta\_0$. Speichern Sie das Resultat in `beta0`.

*** =pre_exercise_code
```{r}
set.seed(2)
n <- 105
x <- runif(n,0,24)
y <- rep(NA,n)
for(i in 1:n) {
  y[i] <- 100 + 60 * x[i] + rnorm(1, sd=20*x[i])
}
plot(x,y, pch=20, col="Steelblue", cex=0.5, xlim = c(0,24), ylim = c(0,1500), xlab="Zeitaufwand", ylab="XP")
```

***=hint


***=sample_code
```{r}
# Berechnen Sie den Schätzer, speichern sie das Ergebnis in beta0

```

***=solution
```{r}
```

*** =sct
```{r}
```

--- type:NormalExercise lang:r xp:100 skills:1 key:db0eb31b7a
## Übung macht den Meister 

Beim Betrachten der Daten kommt Ihnen etwas merkwürdig vor: Es scheint so, als ob die im Mittel erzielte XP nicht wesentlich vom investierten Zeitaufwand abhängt.

*Die Vektoren `XP` und `Z` sind in Ihrer Arbeitsumgebung verfügbar.*

*** =pre_exercise_code
```{r}
set.seed(2)
n <- 300
x <- rnorm(n)
Z <- runif(n,0,24)
u <- (10+5*Z)*rnorm(n,sd=6)
XP <- 500 + 60*x + u
plot(Z[XP<=1500&XP>=150],XP[XP<=1500&XP>=150], pch=20, col="steelblue", xlab="Zeitaufwand", ylab="XP", ylim = c(0,1500))
```




