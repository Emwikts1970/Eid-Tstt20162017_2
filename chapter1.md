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
beta0 <- lm(y ~ x) 
```

*** =sct
```{r}
test_object(beta0)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
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
# Berechnen Sie den Schätzer, speichern sie die Ergebnisse in beta0 und beta1.

```

***=solution
```{r}
```

*** =sct
```{r}
```

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Heteroskedastie I

In der letzten Aufgabe sind Sie zu dem Schluss gekommen, dass der Koeffizient $\beta\_0$ im Regressionsmodell

$$ XP\_i = \beta\_0 + \beta\_1 \times Z\_i +  \epsilon\_i $$

zum $5\%$-Niveau nicht signifikant von $0$ verschieden ist, wenn ein *nur bei Homoskedastie* konsistenter Standardfehler berechnet wird.

Betrachten Sie erneut den Plot: Eine weitere Auffälligkeit in den Daten ist, dass die Streuung der erreichten XP mit dem investierten Zeitaufwand zunimmt, d.h. es liegt Heteroskedastie vor.
<br>
Sie sind besorgt über die Korrektheit der zuvor getroffenen Schlussfolgerung bzgl. der Signifikanz von $\beta\_0$ und wollen daher den Test mit heteroskedastie-robusten Standardfehlern wiederholen.

*Die Vektoren `XP` und `Z` sowie das Modell `mod` aus der letzten Aufgabe sind in Ihrer Arbeitsumgebung verfügbar.*


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

- Laden Sie das Paket `sandwich`.
- Führen Sie zunächst eine heteroskedastie-robuste Schätzung der Varianz-Kovarianz-Matrix der Regressionskoeffizienten durch. Speichern Sie die Matrix in `hcm`.
- Vergewissern Sie sich, dass es sich bei `hcm` um eine symmetrische $2\times 2$-Matrix handelt.


***=hint

Für Heteroskedastie robuste Schätzung der Varianz-Kovarianz-Matrix von Regressionskoeffizienten können Sie die Funktion `vcovHC` benutzen.

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Heteroskedastie II

***=instructions

- Laden Sie nun zusätzlich das Paket `lmtest`
- Führen Sie erneut einen Signifikanztest für $\beta\_0$ durch. Benutzen Sie dafür die Funktion `coeftest` in Kombination mit dem robusten Schätzer für die Varianz-Kovarianz-Matrix der geschätzten Koeffizienten aus der letzten Aufgabe 
- Zeigen Sie mit logischen Operatoren, dass die robuste $t$-Statistik im Ablehnbereich für einen Test zum $5\%$-Niveau liegt und sich damit eine andere Schlussfolgerung als bei herkömmlichen Standardfehlern ergibt. 

***=sample_code
```{r}
# Laden Sie das Paket lmtest


# Benutzen Sie die Funktion coeftest


# Zeigen Sie, dass die robuste t-Statistik im Ablehnbereich liegt


```

--- type:NormalExercise lang:r xp:100 skills:1 key:726a6d460b
## Ein Linear Unverzerrter Schätzer

Angenommen Sie betrachten das Regressionsmodel

$$ y\_i=\beta\_0 + \epsilon\_i $$

d.h. eine Regression der variable $Y$ auf eine Konstante. Anders gesagt: Der einzige Regressor ist ein Vektor mit Einsen

$$X = (1 \dots 1)'.$$

In `script.R` finden Sie eine Funktion, welchen den OLS-Schätzer für $\beta\_0$ in diesem Modell berechnen soll. Allerdings ist die Funktion fehlerhaft programmiert: Dieser Schätzer ist zwar linear aber *nicht unverzerrt* und entspricht nicht der OLS-Lösung.

*** =instructions

Passen Sie den Code der Funktion `OLS` im `script.R` an, sodass der OLS-Schätzer für $\beta\_0$ numerisch korrekt berechnet wird.

*** =pre_exercise_code
```{r}

```

***=sample_code

```{r}
OLS <- function(Y) {
    beta0 <- 1/length(Y)*sum(Y)+rlnorm(sd(Y))
    return(beta0)
} 
```

*** =sct
```{r}

```

--- type:MultipleChoiceExercise lang:r xp:100 skills:1 key:726a6d460b
## A Simulation Study I

Suppose you got the regression model

$$ y=\beta + \epsilon $$

i.e. a regression of some variable $y_i$ solely on a constant or, put differently: the regressor is a vector of ones

$$\mathbf{X} = (1 \dots 1)'.$$

In the plotting area on the right You see the result of a *Monte Carlo Simulation* analysing distributional properties of the OLS estimator for $ \beta $ in the model above and another linear estimator $\overset{\sim}{\beta}$ which uses different weights than OLS. Say, $\beta=0$. 

Is the result consistent with what You expect beeing aware of the Gauss-Markov Theorem?  

*** =instructions
- Yes, both estimators seem to be unbiased but the OLS estimator has less dispersion.
- No, the distribution of $\overset{\sim}{\beta}$ looks more like a standard normal distribution.
- Cannot be answered without prior inspection of the underlying data.

*** =pre_exercise_code
```{r}
# Set sample size and number of repititionas

n <- 100      
reps <- 1e5

# Choose epsilon and create a vector of weights as defined above

epsilon <- 0.8
w <- c( rep((1+epsilon)/n,n/2), rep((1-epsilon)/n,n/2) )

# Draw random sample y_1,...,y_N from the standard normal distribution 
# Compute both estimates 1e6 times and store the result in vectors  

ols <- rep(NA,reps)
weightedestimator <- rep(NA,reps)

custom_seed(1234)
for (i in 1:reps)
{
  y <- rnorm(n)
  ols[i] <- mean(y)
  weightedestimator[i] <- crossprod(w,y)
}

# Plot estimates of the estimators distribution 

plot(density(ols),col="purple", lwd=3, main="Density of OLS and Weighted Estimator",xlab="")
lines(density(weightedestimator),col="steelblue", lwd=3) 
abline(v=0,lty=2)
legend('topright', c("OLS","Weighted"), col=c("purple","steelblue"),lwd=3)
```
*** =sct
```{r}
msg_bad <- "That is not correct!"
msg_success <- "Exactly!"
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))
```


