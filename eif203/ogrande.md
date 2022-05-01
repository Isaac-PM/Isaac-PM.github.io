---
title: "Formalización cota superior asintótica: O(), Ω() y Θ()"
author: "Isaac Palma Medina"
---

# Formalización cota superior asintótica: O(), Ω() y Θ()

***

## O()

> f ~ O(g) sii ∃ n<sub>0</sub> >= 0, ∃ c > 0 : f(n) <= cg(n) ∀ n >= n<sub>0</sub>

Función **g** que multiplicada por una constante **c** apartir de un punto (n<sub>0</sub>) es mayor o igual a **f**.

> ∴ f crece a lo más como g hasta por una constante

### Representación gráfica

<center><img src="/eif203/images/ogrande.jpg" width=""/></center>

### Ejemplo

> f(n) = 5n<sup>2</sup> + 8

> g(n) = n<sup>2</sup>

#### Desarrollo

> Prueba que f ~ O(g)

> 5n<sup>2</sup> + 8 ~ O(n<sup>2</sup>)

Se debe encontrar n<sub>0</sub> y **c**

> 5n<sup>2</sup> <= n<sup>2</sup>, el elemento de **f** debe ser igual o inferior al elemento de **g**

> 5n<sup>2</sup> <= 5n<sup>2</sup> ∀ n>= 0, se le añade 5 para que la anterior condición sea cierta ("ayudarle")

> 8 <= n<sup>2</sup>, el **otro** elemento de **f** debe ser igual o inferior al elemento de **g**

> 8 <= n<sup>2</sup> ∀ n>= 3, se modifica el rango para que la expresión sea cierta, ya que 8 <= n<sup>2</sup>, n = 3, 8 <= 3<sup>2</sup>, 8 <= 9

Conclusión

> 5n<sup>2</sup> <= 5n<sup>2</sup> ∀ n>= 0

> 8 <= n<sup>2</sup> ∀ n>= 3

> Se suman los elementos de cada lado 5n<sup>2</sup> + 8 <= 5n<sup>2</sup> + n<sup>2</sup> 

> ∴ 5n<sup>2</sup> + 8 <= 6n<sup>2</sup> ∀ n>= 3

> ∴ c = 6 y n<sub>0</sub> = 3, **c** es el valor de la constante que multiplica **g** y **n<sub>0</sub>** es el valor mínimo del rango para que la expresión sea cierta

> ∴ 5n<sup>2</sup> + 8 ~ O(n<sup>2</sup>)

## Ω()

> f ~ Ω(g) sii g ~ O(f)

Función **g** que multiplicada por una constante **g** sea menor que **f** desde un punto n<sub>0</sub>.

> ∴ f crece al menos como g hasta por una constante, **f >= cg**

### Representación gráfica

<center><img src="/eif203/images/omegagrande.jpg" width=""/></center>

### Ejemplo

> f(n) = 5n<sup>2</sup> + 8

> g(n) = n<sup>2</sup>

> Se tiene que 5n<sup>2</sup> + 8 >= n<sup>2</sup> ∀ n>= 0, eso es cierto

> c = 1 y n<sub>0</sub> = 0

> ∴ 5n<sup>2</sup> + 8 ~ Ω(n<sup>2</sup>)

## Θ()

> f ~ Θ(g) sii f ~ Ω(g) ^ f ~ O(g)

Función que al **probar ambos casos**, resulta que tiene una cota O(g) y Ω(g) al mismo tiempo, dando lugar a dos **funciones g**, con distintas constante **c** y dsintintos puntos **n<sub>0</sub>**.

### Representación gráfica

<center><img src="/eif203/images/thetagrande.jpg" width=""/></center>

### Ejemplo

> f(n) = 5n<sup>2</sup> + 8

> g(n) = n<sup>2</sup>

Conclusión

> a) f ~ O(n<sup>2</sup>)

> b) f ~ Ω(n<sup>2</sup>)

> ∴ 5n<sup>2</sup> + 8 ~ Θ(n<sup>2</sup>)

# Teoremas

Sea **1** : n → 1, tal que:

<center><img src="/eif203/images/uno.jpg" width=""/></center>

1. c ~ O(1) ∀ c > 0
2. f<sub>1</sub> + f<sub>2</sub> ~ O( max(f<sub>1</sub>, f<sub>2</sub>) )
3. f<sub>1</sub> * f<sub>2</sub> ~ O( O(f<sub>1</sub>), O(f<sub>2</sub>) )
4. Si <img src="https://latex.codecogs.com/png.image?\inline&space;\large&space;\dpi{100}\bg{white}\sum_{k&space;=&space;0}^{d}&space;a_{k}n^{k},&space;a_{d}&space;\neq&space;0" title="https://latex.codecogs.com/png.image?\inline \large \dpi{100}\bg{white}\sum_{k = 0}^{d} a_{k}n^{k}, a_{d} \neq 0" /> (un polinomio)
   1. f ~ O(n<sup>d</sup>), se usa al monomio más grande

# Jerarquía

## Intratables

1. n<sup>n</sup>
2. n!
3. 2<sup>n</sup>

## Tratables

1. n<sup>k</sup>, k > 1
2. nlog(n)
3. n
4. log(n)
5. c

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**