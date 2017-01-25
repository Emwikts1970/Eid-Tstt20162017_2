---
  title       : Aufgaben
description : Dieses Testat besteht aus einem Kapitel mit insgesamt 11 Aufgaben. Die Aufgaben können unabhängig voneinander gelöst werden. Wir empfehlen Ihnen jedoch die Bearbeitung in der vorgegebenen Reihenfolge. <br> Beachten Sie, dass gelöste Aufgaben abhängig vom Schwierigkeitsgrad mit 100XP, 150XP oder 200XP belohnt werden. Lösungen, die bis 20 Uhr eingereicht sind werden akzeptiert.

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Testatpunkte

Erinnern Sie sich an das letzte Testat: Es waren 1500XP zu erreichen. Angenommen Sie arbeiten als unterbezahlter Hiwi am Lehrstuhl für Ökonometrie und Ihnen liegen Beobachtungen zur erreichten XP (`XP`) sowie investierter Zeit (`Z`) vor. In ihrer Schusseligkeit haben Sie einen zufälligen Teil der Daten unwiederbringlich gelöscht und müssen nun Regressionsanalyse & Inferenzstatistik anhand einer Stichprobe betreiben. Professor Dr. Prank pocht auf signifikante Ergebnisse!
<br>
Der beobachtete Zusammenhang wird im Plot-Panel dargestellt.

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

***=sample_code
```{r}
# Berechnen Sie den Schätzer, speichern Sie das Ergebnis in beta0 und beta1

```

***=solution
```{r}
beta <- 2
```

*** =sct
```{r}
test_object("beta")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Übung macht den Meister? 

Sie befassen sich weiterhin mit dem Modell

$$ XP\_i = \beta\_0 + \beta\_1 \times Z\_i +  \epsilon\_i. $$

Beim Betrachten des Plots kommt Ihnen etwas merkwürdig vor: Es scheint so, als ob die im Mittel erzielte XP zwar mit der investierten Zeit steigt, allerdings scheinen Studenten ohne Vorbereitungszeit mehr als 100XP zu erzielen.

Nun interessiert es Sie, ob die erwartete Punktzahl für Studenten, die gar keine Zeit investiert haben, signifikant von $0$ verschieden ist. Hierzu möchten Sie einen $t$-Test durchführen.

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
## Ein Linearer und Unverzerrter Schätzer?

Angenommen Sie betrachten das Regressionsmodel

$$ y\_i=\beta\_0 + \epsilon\_i \ \ , \ \ \epsilon \sim (0,\sigma^2) $$

d.h. eine Regression der variable $Y$ auf eine Konstante. Anders gesagt: Der einzige Regressor ist ein Vektor mit Einsen

$$\mathbf{X} = (1 \dots 1)'.$$

In `script.R` finden Sie eine Funktion, welche den OLS-Schätzer für $\beta\_0$ in diesem Modell berechnen soll. Allerdings ist die Funktion fehlerhaft programmiert: Dieser Schätzer ist zwar linear aber *nicht unverzerrt* und entspricht nicht der OLS-Lösung.

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

--- type:NormalExercise lang:r xp:100 skills:1 key:726a6d460b
## Ein Linearer und Unverzerrter Schätzer! 

Betrachten Sie weiterhin das Regressionsmodell

$$ Y\_i=\beta\_0 + \epsilon\_i \ \ , \ \ \epsilon \sim (0,\sigma^2). $$

Aus der Vorlesung wissen Sie, dass ein Schätzer $\overset{\sim}{\beta}$ mit

$$ \overset{\sim}{\beta} = \sum\_{i=1}^n a\_i y\_i \ \ \text{und} \ \ \text{E}(\overset{\sim}{\beta}|X\_1,\dots, X\_n)=\beta $$

als linear und unverzerrt bezeichnet wird.
<br>
In dieser Aufgabe sollen Sie eine Schätzfunktion für $\beta\_0$ erstellen deren Gewichte $a\_i$ von denen der OLS-Lösung abweichen, genauer

$$ \overset{\sim}{\beta}\_w = \sum\_{i=1}^n w\_i Y\_i \ \ \text{wobei} \ \ w_i = \begin{cases}
\frac{1 + \epsilon}{n} & \text{wenn} \ n \leq n/2 \\\\ 1/n & \text{sonst.} \end{cases} $$

Weiterhin gelte $\epsilon = 0.8$.

*** =instructions
Betrachten Sie den vorgegebenen Code in `script.R`. Wie müssen Sie den Vektor der Gewichte `w` definieren? Ersetzen Sie `???` mit dem korrekten Ausdruck! <br> <b>Hinweis</b>: Benutzen Sie die Funktion `rep`, siehe `?rep`.


***=sample_code

```{r}

beta.w <- function(Y) {
    n <- length(Y)
    w <- ???
    return(crossprod(w,y)) # Skalarprodukt von w und y
}

```

--- type:NormalExercise lang:r xp:100 skills:1 key:726a6d460b
## Das Gauss-Markov-Theorem I

Erinnern Sie sich an die Aussage des Gauss-Markov-Theorems:
<br>
<br>
Sind die klassischen OLS-Annahmen erfüllt und die Fehlerterme homoskedastisch, so ist der OLS-Schätzer am effizientesten in der Klasse der linearen und bedingt unverzerrten Schätzer, d.h. es gibt keinen anderen qualifizierten Schätzer mit einer geringeren Varianz.

Sie sollen dies Anhand einer Simulationsstudie für die zuvor erstellten Schätzfunktionen `OLS` und `betaw` verdeutlichen:

Die Simulation soll die folgenden Arbeitsschritte umfassen:

1. Erstellen Sie einen Vektor `Y` mit 100 Zufallszahlen aus einer $\mathcal{N}(0,1)$-Verteilung.
2. Berechnen Sie die Schätzer mit den Funktionen `OLS` und `beta.w`. Speichern Sie die Resultate jeweils an der $i$-ten Stelle der Vektoren `ols` und `weighted.w` ab.
3. Wiederholen Sie die Schritte 1. und 2. für $i=1,\dots,100$

*Die Funktionen `OLS` und `betaw` sind in ihrer Arbeitsumgebung verfügbar!*

***=instructions
- Initialisieren Sie zunächst die Vektoren `ols` und `weighted.w`, sodass beide Vektoren $100$ Einträge `NA` aufweisen.
- Ein Code-Gerüst für die obige Prozedur ist vorgegeben. Ersetzen Sie die `???` mit den korrekten Ausdrücken!

***=sample_code
```{r}
custom_seed(1234) # nicht von Relevanz

# Initialisieren Sie die Vektoren ols und weighted.w


# Simulation
for (i in 1:???) {
  y <- ???
  ols[???] <- ???
  weighted.w[???] <- ???
}
```

*** =pre_exercise_code
```{r}
# Set sample size and number of repititionas

n <- 100      
reps <- 10

# Choose epsilon and create a vector of weights as defined above

epsilon <- 0.8
w <- c(rep((1+epsilon)/n,n/2),rep(1/n,n/2))

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

--- type:NormalExercise lang:r xp:100 skills:1 key:726a6d460b
## Das Gauss-Markov-Theorem I

Betrachten Sie nun Ihre Ergebnisse aus der letzten Aufgabe genauer. 
Gemäß dem Gauss-Markov-Theorem können Sie erwarten, dass 
$$ \text{Var}(\widehat{\beta}\_{OLS}) \leq \text{Var}(\overset{\sim}{\beta}\_{w}).  $$


