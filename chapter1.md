---
  title       : Aufgaben
description : Dieses Testat besteht aus einem Kapitel mit insgesamt 11 Aufgaben. Die Aufgaben können unabhängig voneinander gelöst werden. Wir empfehlen Ihnen jedoch die Bearbeitung in der vorgegebenen Reihenfolge. <br> Beachten Sie, dass gelöste Aufgaben abhängig vom Schwierigkeitsgrad mit 100XP, 150XP oder 200XP belohnt werden. Lösungen, die bis 20 Uhr eingereicht sind werden akzeptiert.

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Testatpunkte

Erinnern Sie sich an das letzte Testat: Es waren 1500XP zu erreichen. Angenommen Sie arbeiten als unterbezahlter Hiwi am Lehrstuhl für Ökonometrie und Ihnen liegen Beobachtungen zur erreichten XP (`XP`) sowie investierter Zeit (`Z`) vor. In ihrer Schusseligkeit haben Sie einen zufälligen Teil der Daten unwiederbringlich gelöscht und müssen nun Regressionsanalyse & Inferenzstatistik anhand einer Stichprobe betreiben. Der Zusammenhang wird im Plot-Panel dargestellt.

Sie interessieren sich für das folgende Model:

$$ XP\_i = \beta\_0 + \beta\_1 \times Z\_i +  \epsilon\_i  $$

*Die Vektoren `XP` und `Z` sind in Ihrer Arbeitsumgebung verfügbar.*

***=instructions

Berechnen Sie die OLS-Schätzer für $\beta\_0$ und $\beta\_1$. Speichern Sie die Ergebnisse in `beta0` und `beta1`.

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
# Berechnen Sie den Schätzer, speichern sie das Ergebnis in beta0 und beta1.

```

***=solution
```{r}
```

*** =sct
```{r}
```

--- type:NormalExercise lang:r xp:100 skills:1 key:20c992f06d
## Übung macht den Meister? 

Sie befassen sich weiterhin mit dem Modell

$$ XP\_i = \beta\_0 + \beta\_1 \times Z\_i +  \epsilon\_i. $$

Beim Betrachten des Plots kommt Ihnen etwas merkwürdig vor: Es scheint so, als ob die im Mittel erzielte XP zwar mit der investierten Zeit steigt, allerdings scheinen Studenten ohne Vorbereitungszeit mehr als 100XP zu erzielen.

Nun interessiert es Sie, ob die erwartete Punktzahl für Studenten, die gar keine Zeit investiert haben, signifikant von 0 verschieden ist. Hierzu möchten Sie einen $t$-Test durchführen.

*Die Vektoren `XP` und `Z` sind in Ihrer Arbeitsumgebung verfügbar.*

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

***=instructions

- Berechnen Sie zunächst die passende $t$-Statistik zum Test $H\_0: \beta\_0=0 \ vs \ H\_1: \beta\_0\neq 0$. Speichern Sie das Ergebnis in `tstat`
- Überprüfen Sie anhand logischer Operatoren, ob der Absolutbetrag von `tstat` den kritischen Wert zum $5\%$-Niveau überschreitet. 

***=hint


***=sample_code
```{r}
# Berechnen Sie den Schätzer, speichern sie das Ergebnis in beta0 und beta1.

```

***=solution
```{r}
```

*** =sct
```{r}
```

--- type:NormalExercise lang:r xp:100 skills:1 key:4c69aaa88d
## Signifikant verschieden




