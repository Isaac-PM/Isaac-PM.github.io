---
title: "HLCC(2), resolución RR"
author: "Isaac Palma Medina"
---

# HLCC(2), resolución RR

Se trabajan funciones sencillas, con una **forma general**. Dichas funciones **fáciles de resolver** se denominan **Homogéneas Lineales de Coeficientes Constantes de Grado Dos (HLCC(2))**.

La **"L"** en las siglas indica que de `n` se pasa a `n - 1` ó a `n - 2` y estos elementos se unen **sumando**.

Las **"CC"** hacen referencia a que los elementos no pueden estar multiplicados por valores no constantes. **Por ejemplo:**

> f<sub>n</sub> = nf<sub>n - 1</sub> + f<sub>n - 2</sub>

La anterior, no cumple con los requisitos para ser considerada una HLCC(2), ya que el primer coeficiente no es constante (es `n`).

### Otro ejemplo:

> f<sub>n</sub> = 3f<sub>n - 1</sub> * f<sub>n - 2</sub>

La anterior, tampoco cumple con los requisitos para ser considerada una HLCC(2), ya que los elementos de la función no se ven unidos por una suma.

### Otro ejemplo:

> f<sub>n</sub> = 3f<sub>n/2</sub> * f<sub>n - 1</sub>

La anterior, no cumple con los requisitos, ya que sus elementos no van desde `n`  hasta `n - 1` ó `n - 2`, sino que hay uno indicado como `n/2`.

Además, después de las llamadas recursivas, **no deben aparecer** alrededor expresiones no recursivas, por **ejemplo**:

> f<sub>n</sub> = nf<sub>n - 1</sub> + f<sub>n - 2</sub> + 2<sup>n</sup>

La anterior se denota como una **expresión no homogénea**. Las expresiones que si cumplen, se denominan **homogéneas** y hacen referencia a la **"H"** en HLCC(2).

> f<sub>n</sub> = nf<sub>n - 1</sub> + f<sub>n - 2</sub> + 1

La anterior se conoce como **Hanoi**, y no cumple con los requisitos para considerarse **"fácil"**.

## Resolución de una HLCC(2)

1. Dada una HLCC(2) de la forma:

> f<sub>n</sub> = af<sub>n - 1</sub> + bf<sub>n - 2</sub>
> f<sub>0</sub> y f<sub>1</sub>

{:start="2"}
2. Encontrar el **polinomio característico**  de la RR, denotado **pc(x)**:
> pc(x) = x<sup>2</sup> - ax - b
   1. Primeramente se escribe: x<sup>2</sup>
   2. Después a se hace un cambio de signo a la constante de f<sub>n - 1</sub> y se añade una equis: -ax
   3. Finalmente se cambia el signo a la constante de f<sub>n - 2</sub> y se designa como la constante de la cuadrática: -b
   4. > pc(x) = x<sup>2</sup> - ax - b

{:start="3"}
3. Resolver **pc(x)**, raíces:
   1. **Primer caso:** las raíces son distintas, r<sub>1</sub> != r<sub>2</sub>:
      1. > Solución: f<sub>n</sub> = αr<sub>1</sub><sup>n</sup> + βr<sub>2</sub><sup>n</sup>, para todo n mayor o igual a 0
      2. Donde en lo anterior, alfa y beta son constantes que dependen de los casos base
   2. **Segundo caso:** las raíces son iguales, r<sub>1</sub> = r<sub>2</sub> = r:
      1. > f<sub>n</sub> = αr<sup>n</sup> + βnr<sup>n</sup>, para todo n mayor o igual a 0
      2. Donde en lo anterior, alfa y beta son constantes que dependen de los casos base

{:start="4"}
4. Resolución del paso 2:

### Ejemplo:

> Dada: f<sub>n</sub> = 3f<sub>n - 1</sub> - 2f<sub>n - 2</sub>, si n > 1

> Casos base: f<sub>0</sub> = 1 y f<sub>1</sub> = 3

Desarrollo del **polinomio característico**

> pc(x) = x<sup>2</sup> - 3x + 2

> Raíces: pc(x) = (x - 2)(x - 1), r<sub>1</sub> = 2 y r<sub>2</sub> = 1

> Se debe optar por el caso de raíces distintas: f<sub>n</sub> = α2<sup>n</sup> + β1<sup>n</sup>

Se soluciona el caso anterior:

> f<sub>n</sub> = α2<sup>n</sup> + β1<sup>n</sup>

> f<sub>n</sub> = α2<sup>n</sup> + β1

> f<sub>n</sub> = α2<sup>n</sup> + β, para todo n mayor o igual a 0

Se encuentran α y β, usando los casos base:

> Si n = 0 y f<sub>0</sub> = 1 entonces f<sub>0</sub> debe ser igual a α2<sup>n</sup> + β

> 1 = α2<sup>0</sup> + β

> 1 = α + β

> Si n = 1 y f<sub>1</sub> = 3 entonces f<sub>1</sub> debe ser igual a α2<sup>n</sup> + β

> 1 = α2<sup>1</sup> + β

> 3 = α2 + β

Se obtiene un sistema de ecuaciones:

> 1 = α + β 

> 3 = α2 + β

> Empezando por la primera: 1 = α + β -> 1 - β = α 

> Sustituyendo en la segunda: 3 = (1 - β)2 + β -> 3 = 2 - 2β + β -> 3 = 2 - β -> β = -1

> Regresando a la primera: 1 = α + β -> 1 = α + -1 -> α = 2

Respuesta:

> f<sub>n</sub> = 2 * 2<sup>n</sup> + - 1

> f<sub>n</sub> = 2<sup>n - 1</sup> - 1

> f<sub>n</sub> = 2<sup>n - 1</sup> - 1, para todo n mayor o igual a 0

Crecimiento:

> f<sub>n</sub> = 2<sup>n - 1</sup> - 1, el 1 se descarta por ser una constante que no aporta al crecimiento

> f<sub>n</sub> = 2<sup>n - 1</sup> -> f<sub>n</sub> = 2<sup>n</sup> * 2<sup>1</sup>, el 2<sup>1</sup> también puede ser descartado

> f<sub>n</sub> = 2<sup>n</sup>

> f<sub>n</sub> ~ O(2<sup>n</sup>)

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**