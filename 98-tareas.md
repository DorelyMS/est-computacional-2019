
# Tareas {-}



* Las tareas se envían por correo a teresa.ortiz.mancera@gmail.com con título: 
EstComp-TareaXX (donde XX corresponde al número de tarea, 01..). 

* Las tareas deben incluir código y resultados (si conocen [Rmarkdown](https://rmarkdown.rstudio.com) 
es muy conveniente para este propósito).

## 1. Instalación y visualización {-}

#### 1. Instala los siguientes paquetes (o colecciones): {-}

* tidyverse de CRAN (`install.packages("tidyverse")`)
* devtools de CRAN (`install.packages("devtools")`)
* gapminder de CRAN (`install.packages("gapminder")`)
* estcomp de GitHUB (debes haber instalado devtools y correr 
`devtools::install_github("tereom/estcomp")`)
* mxmaps **instalarlo es opcional** de [GitHub](https://github.com/diegovalle/mxmaps#installation)


#### 2. Visualización {-}

* Elige un base de datos, recuerda que en la ayuda puedes encontrar más 
información de las variables (`?gapminder`): 
    + gapminder (paquete `gapminder` en CRAN).
    + election_2012 ó election_sub_2012 (paquete `estcomp`).
    + df_edu (paquete `estcomp`).
    + enlacep_2013 o un subconjuto de este (paquete `estcomp`).

* Escribe algunas preguntas que consideres interesantes de los datos.

* Realiza $3$ gráficas buscando explorar las preguntas de arriba y explica las
relaciones que encuentres. Debes usar lo que revisamos en estas notas y al menos
una de las gráficas debe ser de paneles (usando `facet_wrap()` o `facet_grid`).

#### 4. Prueba (en clase)! {-}

Ejercicios basados en ejercicios de @r4ds.

Socrative: https://b.socrative.com/login/student/  
Room: ESTCOMP


```r
library(tidyverse,warn.conflicts = FALSE, quietly = TRUE)
library(gridExtra)

# 1.
one <- ggplot(data = mpg) +
  geom_smooth(mapping = aes(x = displ, y = hwy))

# 2.
two <- ggplot(data = mpg) +
  geom_smooth(mapping = aes(x = displ, y = hwy), se = FALSE)

# 3.
three <- ggplot(data = mpg) +
  geom_smooth(mapping = aes(x = displ, y = hwy, group = drv))
```

<img src="98-tareas_files/figure-html/unnamed-chunk-3-1.png" width="720" style="display: block; margin: auto;" />



```r
# 4. 
four <- ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy, color = "blue"), 
    show.legend = FALSE)

# 5.
five <- ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy), color = "blue", 
    show.legend = FALSE)

# 6. 
six <- ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy), color = "class", 
    show.legend = FALSE)

# 7.
seven <- ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy, color = "class"), 
    show.legend = FALSE)
```



<img src="98-tareas_files/figure-html/unnamed-chunk-5-1.png" width="672" style="display: block; margin: auto;" />



```r
eight <- ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + 
  geom_point() + 
  geom_smooth()

nine <- ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(aes(color = drv)) + 
  geom_smooth(data = select(mpg, displ, hwy), aes(x = displ, y = hwy))

ten <- ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(aes(color = drv)) +
  geom_smooth()

eleven <- ggplot(data = mpg) + 
  geom_point(aes(x = displ, y = hwy, color = drv)) + 
  geom_smooth(aes(x = displ, y = hwy, color = drv))
```

## 2. Transformación de datos {-}

1. Vuelve a instalar el paquete `estcomp` para asegurar que tengas todos los
datos y su documentación: `devtools::install_github("tereom/estcomp")`

2. Usaremos los datos `df_edu`, ve la ayuda para entender sus variables:


```r
library(estcomp)
?df_edu
```

  * ¿Cuál es el municipo con mayor escolaridad promedio (valor de `schoolyrs`)?
    Tip: usa `filter` para quedarte únicamente con `sex` correspondiente a 
    `Total`.
  
  * Crea una `data.frame` que contenga una línea por cada estado y por sexo, con 
  la siguiente información:
    + la escolaridad promedio por estado y sexo (ponderada por la población 
    `pop_15`)
    + la población de cada sexo (mayor a 15 años)
  
  * Crea una variable que indique el porcentaje de la población que cursó al 
  menos educación básica. 
  
  * Enuncia al menos una pregunta que se pueda responder transformando y 
  graficando estos datos. Crea tu(s) gráfica(s).
  


