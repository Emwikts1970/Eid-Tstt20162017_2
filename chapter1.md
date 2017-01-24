---
  title       : Aufgaben
description : Dieses Testat besteht aus einem Kapitel mit insgesamt 11 Aufgaben. Die Aufgaben können unabhängig voneinander gelöst werden. Wir empfehlen Ihnen jedoch die Bearbeitung in der vorgegebenen Reihenfolge. <br> Beachten Sie, dass gelöste Aufgaben abhängig vom Schwierigkeitsgrad mit 100XP, 150XP oder 200XP belohnt werden. Lösungen, die bis 20 Uhr eingereicht sind werden akzeptiert.

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Testatpunkte


Erinnern Sie sich an das letzte Testat: Es waren 1500XP zu erreichen. Angenommen Sie arbeiten als unterbezahlter Hiwi am Lehrstuhl für Ökonometrie und Ihnen liegen Beobachtungen zur erreichten XP sowie investierter Zeit vor. Der Zusammenhang wird im Plot-Panel dargestellt.
<br>
Professor Prank verlangt von Ihnen 




***=instructions

Replace the `???` and create the dummy regressor `D` using the proposed loop above.


*** =pre_exercise_code
```{r}
set.seed(2)
n <- 300
x <- rnorm(n)
z <- runif(n,0,24)
u <- (10+5*z)*rnorm(n,sd=6)
y <- 500 + 60*x + u
plot(z[y<=1500&y>=150],y[y<=1500&y>=150], pch=20, col="steelblue", xlab="Zeitaufwand", ylab="XP", ylim = c(0,1500))


```

***=hint


***=sample_code
```{r}
# Create D

```

***=solution
```{r}
```

*** =sct
```{r}
```

