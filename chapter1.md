---
  title       : Aufgaben
description : Dieses Testat besteht aus einem Kapitel mit insgesamt 11 Aufgaben. Die Aufgaben können unabhängig voneinander gelöst werden. Wir empfehlen Ihnen jedoch die Bearbeitung in der vorgegebenen Reihenfolge. <br> Beachten Sie, dass gelöste Aufgaben abhängig vom Schwierigkeitsgrad mit 100XP, 150XP oder 200XP belohnt werden. Lösungen, die bis 20 Uhr eingereicht sind werden akzeptiert.

--- type:NormalExercise lang:r xp:100 skills:1 key:c4b2c27865
## Schleife & Dummy

Erinnern Sie sich an das letzte R-Testat: Sie haben eine Dummyregression des Stundenlohns auf das Geschlecht durchgeführt.

In dieser Aufgabe sollen Sie sich mit dem folgenden Zusammenhang befassen:




Instead of using the regressor $CS$, we might be interested in running a regression where the regressor, $D$ say, is binary variable or a so-called dummy variable. 

For example, we may define $D_i$ in the following way:

$$ D_i = \begin{cases} 1 \ \ \text{if $CS$ in the $i^{th}$ class < 26} \\\\ 0 \ \ \text{if $CS$ in the $i^{th}$ class $\geq$ 26} \end{cases} $$

Using R, one way to do this is as follows:

```{r}
# Define an empty vector D
D <- c()
# Assign values accordingly using a loop
for (i in 1:length(cs)) {
  if (cs[i] < ???) { 
    D[i] <- ???
    } else {
      D[i] <- 0
    }
  }
```

Notice that the code above contains two gaps indicated by `???`. Can You replace them with the right expressions?

<br>
*Vectors `cs` and `ts` are availabe in Your working environment.*
<br>

***=instructions

Replace the `???` and create the dummy regressor `D` using the proposed loop above.


*** =pre_exercise_code
```{r}
cs <- c(23, 19, 30, 22, 23, 29, 35, 36, 33, 25)
ts <- c(430, 430, 333, 410, 390, 377, 325, 310, 328, 375)
```

***=hint


***=sample_code
```{r}
# Create D

```

***=solution
```{r}
## Create D
# Define an empty vector D
D <- c()
# Assign values accordingly using the loop
for (i in 1:length(cs)) {
  if (cs[i] < 26) { 
    D[i] <- 1
    } else {
      D[i] <- 0
    }
  }
```

*** =sct
```{r}
test_student_typed("for (i in 1:length(cs)) {
  if (cs[i] < 26) { 
    D[i] <- 1
    } else {
      D[i] <- 0
    }
  }", not_typed_msg="Make sure You use the loop proposed above. If you have done so, check Your replacement for both `???`.")
test_object("D")
```

