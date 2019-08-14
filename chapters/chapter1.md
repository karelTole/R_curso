---
title: 'Capítulo 1: La Magia de ggplot2' 
description: Aprenda cómo ggplot2 convierte las variables en gráficos estadísticos
prev: null
next: /capítulo2
id: 1
type: capítulo
---
<exercise id="1" title="Data Frame, Introducción rápida">

Repasemos los conceptos básicos de `data.frame`s.

Un `data.frame` es básicamente un formato de tabla que tiene las siguientes propiedades:

<img src="tidy-1.png">

- Cada columna puede tener un tipo diferente (`numérico`,` carácter`, `booleano`,` factor`)
- Las columnas se llaman "variables"
- Las filas corresponden a una sola observación (idealmente)
- Puede ser subconjunto o filtrado según criterios

Se puede acceder a las variables individuales dentro de un `data.frame` con el operador` $ `(como` gap1992 $ pop`). No usaremos esto muy a menudo, ya que el 'tidyverse' nos permite acceder a las variables sin él, como verá.

Ejecute `colnames ()` y `head ()` en los datos `gap1992` para ver qué hay en cada columna. Luego vea cuántas filas hay en el conjunto de datos usando `nrow ()`. Ejecútelos en la consola antes de enviar su respuesta.



<codeblock id="01_01">
</codeblock></exercise>

<exercise id="2" title="Thinking about aesthetics">
Ahora que hemos aprendido un poco sobre el `data.frame`, podemos llegar a la parte divertida: hacer gráficos.

Lo primero que vamos a hacer es pensar en cómo representamos las variables en una gráfica.

¿Cómo representamos visualmente una variable en nuestro conjunto de datos? Echa un vistazo a este gráfico. ¿Qué variable se asigna a `y`, y qué se asigna a` x`, y qué se asigna a `color`?

<img src="gap1992.png">

<choice>
<opt text="x = gdpPercap, y = log(lifeExp), color = continent">
Tienes las cosas invertidas y estás tomando el registro de la variable incorrecta</opt>
<opt text="x = continent, y = year, color = pop">
Variables incorrectas. Regrese y mire lo que se está mapeando</opt>
<opt text="y = lifeExp, x = log(gdpPercap), color = continent" correct = "true">
¡Correcto! Estamos mostrando lifeExp como nuestra variable y y log (gdpPercap) como nuestra variable x</opt>
</choice>
</exercise>

<exercise id="3" title="Mapping variables to produce geometric plots">

Un gráfico estadístico consiste en:

+ Un `mapeo` de variables en` datos` a
+ `aes ()` atributos temáticos de
+ `geom_` objetos métricos.

En código, esto se traduce como:

```{r}
ggplot(data = gap1992, mapping = aes(x = log(gdpPercap), y=log(pop))) +
  geom_point()
```

Tomemos el código de ejemplo anterior aparte. Una llamada `ggplot2` siempre comienza con la función` ggplot () `. En esta función, necesitamos dos cosas:

1. `data` - en este caso,` gap1992`.
2. `mapping '- Un mapeo estético, utilizando la función` aes () `.

Para mapear nuestras variables a propiedades estéticas, necesitaremos usar `aes ()`, que es nuestra función de mapeo teórico `aes ()`. En nuestro ejemplo, asignamos `x` a` log (gdpPercap) `e` y` a `log (pop)`.

Finalmente, podemos superponer nuestra geometría en la gráfica usando `geom_point ()`.

Con base en el gráfico a continuación, asigne las variables apropiadas a la estética `x` e` y`. Ejecuta tu trama. Recuerde, puede intentar trazar en la consola antes de enviar su respuesta.

<img src="gap1992.png">


<codeblock id="01_03">
Mira la gráfica. Si necesita los nombres de las variables, siempre puede usar `head ()` o `colnames ()` en el conjunto de datos `gap1992`.</codeblock></exercise>

<exercise id="4" title="More about aes">
Para `geom_point ()`, hay muchas otras estéticas. Lo importante es saber que
La estética son propiedades de la geom. Si necesitas saber la estética que puedes
asignar a un `geom`, siempre puede usar` help () `(como` help (geom_point) `).

Para obtener una lista de la estética de `geom_point ()`, mire aquí: [http://ggplot.yhathq.com/docs/geom_point.htmlfont>(http://ggplot.yhathq.com/docs/geom_point.html)
y mira todas las asignaciones estéticas.

¿Cuál de los siguientes es * no * una estética asignable a `geom_point ()`?

<choice>
<opt text="`x`">
No exactamente. ¡Necesitas `x` para mapear un punto!</opt>
<opt text="`shape`">
Nope. Esta es una estética asignable a `geom_point ().`</opt>
<opt text="`linetype`" correct = "true">
Correcto. `linetype` no es mapeable a` geom_point () `. Los puntos no tienen un "tipo de línea", ¿verdad?</opt>
</choice>
</exercise>

<exercise id="5" title="Points versus lines">

Lo bueno de `ggplot2` es que es fácil intercambiar representaciones.
En lugar de puntos x-y, podemos trazar los datos como un gráfico lineal intercambiando `geom_line ()`
para `geom_point ()`.

Primero ejecute el código para ver la trama con puntos. Cambie el `geom_point ()` en el siguiente gráfico a `geom_line ()`. ¿Que pasó?
¿Cómo cambió la presentación visual de los datos?



<codeblock id="01_05">
</codeblock></exercise>

<exercise id="6" title="Geoms are layers on a ggplot">

 Cómo se pronuncia

¡No estamos restringidos a una sola geom en un gráfico! Puedes pensar en geoms
como capas en un gráfico. Por lo tanto, podemos usar el símbolo `+` para agregar geoms a nuestro
declaración base `ggplot ()`.

Agregue tanto `geom_line ()` como `geom_point ()` al siguiente ggplot. ¿Son los resultados lo que esperabas?


<codeblock id="01_06">
</codeblock>
</exercise>


<exercise id="7" title="Quick review about ggplot2">

¿Qué hace el `+` en una declaración `ggplot`?

Por ejemplo:

```{r}
ggplot(gap1992, aes(x = log(gdpPercap), y = lifeExp, color=continent)) +
  geom_line() + geom_point()
```

<choice>
<opt text="adds one `data.frame` to another `data.frame` ">
Este no es el caso. Regrese y mire el código ggplot.</opt>
<opt text="allows you to chain data and geoms together into a single statistical graphic" correct="true">
¡Correcto! Así es como podemos agregar datos y capas geoms juntos</opt>
<opt text="allows you to add variables together in a `data.frame`">
Mire el código de ggplot y vea si estamos manipulando datos o no. ¿Estamos?</opt>
</choice>
</exercise>

<exercise id="8" title="Final Challenge: Recreate this Gapminder Plot">

Su desafío final es recrear completamente este gráfico utilizando los datos `gap1992`.

<img src="gap1992.png">

- Si necesita recordar nombres de variables, siempre puede llamar a `head (gap1992)` o `colnames (gap1992)` en la consola.
- Recree el gráfico anterior mapeando las variables correctas a los elementos estéticos correctos. Recuerde, puede intentar trazar en la consola antes de enviar su respuesta.

<codeblock id="01_08">
</codeblock></exercise>

<exercise id="9" title="What you learned in this capítulo">

- Sintaxis básica `ggplot2`.
- Trazar datos x-y usando `ggplot2` usando tanto` geom_point () `como` geom_bar () `.
- Asignación de variables en un conjunto de datos a propiedades visuales usando `aes ()`
- `geom`s corresponden a capas en un gráfico.
- Ese `ggplot2` puede hacer algunos gráficos geniales
- Que puedes hacer esto!

¡Simplemente pasa al siguiente capítulo!

<codeblock id="01_09">
</codeblock></exercise>

