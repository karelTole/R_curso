---
type: slides
---

# Anatomía de una figura ggplot2

---

# Mapeo de variables para producir trazados geométricos

Un gráfico estadístico consiste en:

+ Un `mapeo` de variables en` datos` a
+ `aes ()` atributos temáticos de
+ `geom_` objetos métricos.

En código, esto se traduce como:

`` `r
ggplot (data = gap1992, mapping = aes (x = log (gdpPercap), y = log (pop))) +
  geom_point ()
`` `
---

# Anatomía de una declaración ggplot

`` `r
ggplot (data = gap1992, mapping = aes (x = log (gdpPercap), y = log (pop))) +
  geom_point ()
`` `

Tomemos el código de ejemplo anterior aparte. Una llamada `ggplot2` siempre comienza con la función` ggplot () `. En esta función, necesitamos dos cosas:

1. `data` - en este caso,` gap1992`.
2. `mapping '- Un mapeo estético, utilizando la función` aes () `.

Para mapear nuestras variables a propiedades estéticas, necesitaremos usar `aes ()`, que es nuestra función de mapeo teórico `aes ()`. En nuestro ejemplo, asignamos `x` a` log (gdpPercap) `e` y` a `log (pop)`.

Finalmente, podemos superponer nuestra geometría en la gráfica usando `geom_point ()`.

---

# ¡Vamos a practicar!
