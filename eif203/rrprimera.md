---
title: "Relaciones de recurrencia"
author: "Isaac Palma Medina"
---
# Relaciones de recurrencia

***

# Concepto

Se puede entender una **relación de recurrencia (RR)**, como aquel objeto o función que contenga en su interior una copia de esta. Se dice que esa función es recurrente al presentar esa propiedad. Por ejemplo:

```python
def factorial(n) :
    if n == 1 :
        return 1
    else :
        return (n * factorial(n - 1))
```

La función anterior (`factorial()`), es recursiva, ya que en su interior posee una llamada a si misma.

## Orden de recurrencia

El **orden de recurrencia** es igual a la cantidad total de llamadas que una función se hace a sí misma, `factorial()` es una **RR de orden uno**, en cambio la siguiente función es una **RR de orden dos**:

> f<sub>n</sub> = f<sub>n - 1</sub> + f<sub>n - 2</sub>

## Inconveniente

La **recurrencia** en un código puede consumir demasiador recursos, y ser ineficiente, por lo que se trata de pasar de un **modelo recurrente** a uno **iterativo**, **resolviendo la RR**.

## Caso base

Se dice **caso base** a aquel momento donde la función no presenta más recurrencia, es decir el caso base es aquel donde la función no se llama más a si misma. Por ejemplo en `factorial()`, el caso base es cuando `n` es igual a `1`.

# Resolviendo una RR

## Susitución hacia atrás

La idea de resolver una RR por **sustitución hacia atrás** es empezar en `n` y llegar a los **casos base**.

### Ejemplo sustitución hacia atrás

> S<sub>n</sub> = 6S<sub>n - 2</sub> - 5S<sub>n - 1</sub> + 3 * n + 1

#### Casos base

> S<sub>0</sub> = 0 y S<sub>1</sub> = -5

#### Solución (sustituyendo las RR)

> S<sub>4</sub> = 6S<sub>2</sub> - 5S<sub>3</sub> + 3 * 4 + 1

> 6 * (6S<sub>0</sub> - 5S<sub>1</sub> + 3 * 2 + 1) - 5S<sub>3</sub> + 3 * 4 + 1

> 6 * (6S<sub>0</sub> - 5S<sub>1</sub> + 3 * 2 + 1) -5 * (6S<sub>1</sub> - 5S<sub>2</sub> + 3 * 3 + 1) + 3 * 4 + 1

> 6 * (6 * 0 - 5 * - 5 + 7) - 5 * (6 * - 5 - 5 * (6 * 0 - 5 * - 5 + 7) + 10) + 13

> 6 * 32 - 5 * (-30 - 5 * 32 + 10) + 13

> 192 - 5 * - 180 + 13 = 1105

> S<sub>4</sub> = 1105

### Implementación recursiva

Derivado del método de sustitución hacia atrás (y haciendo uso sobre todo del **SPEC**), se logra programar en **Python** un módulo que implemente la **RR**.

```python
def s_rec(n:int) -> int :
    if n == 0 : # Inclusión de los casos base.
        return 0
    if n == 1 : # Inclusión de los casos base.
        return -5
    return 6 * s_rec(n - 2) - 5 * s_rec(n - 1) + 3 * n + 1 # Llamada recursiva.
```

## Sustitución hacia adelante

Usando la misma función, se puede optar por otro método denominado **sustitución hacia adelante**, el cual parte de **los casos base** para resolver la RR. Se usa una **tabla**, para dicho propósito.

| **-** |         **A**         |          **B**         |      **C**     | **S<sub>n</sub> = A + B + C** |
|:-----:|:---------------------:|:----------------------:|:--------------:|:-----------------------------:|
| **n** |   6S<sub>n - 2</sub>  |   -5S<sub>n - 1</sub>  |     3n + 1     |               -               |
| **1** |           -           |            -           |        -       |               -5              |
| **2** |   6S<sub>0</sub> = 0  |  -5S<sub>1</sub> = 25  |  3 * 2 + 1 = 7 |               32              |
| **3** | 6S<sub>1</sub> = - 30 | -5S<sub>2</sub> = -160 | 3 * 3 + 1 = 10 |              -180             |
| **4** |  6S<sub>2</sub> = 192 |  -5S<sub>3</sub> = 900 | 3 * 4 + 1 = 12 |              1105             |

### Implementación iterativa

De la misma manera que con la sustitución hacia atrás, se puede obtener del proceso anterior una manera de resolver la RR. Sin embargo, la **implementación iterativa no usa recursión**, por lo que necesita de un analisis más profundo del ejercicio. De la siguiente manera:

```python
def s_iter(n:int) -> int :
    if n == 0 : # Inclusión de los casos base.
        return 0
    if n == 1 : # Inclusión de los casos base.
        return -5
    a, b = 0, -5
    for k in range(1, n + 1):
        a, b = b, 6 * a - 5 * b + 3 * (k + 1) + 1
    return a  
```

# HLCC(2) y DyC


![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**