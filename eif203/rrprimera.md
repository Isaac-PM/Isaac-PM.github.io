---
title: "Relaciones de recurrencia"
author: "Isaac Palma Medina"
---
# Relaciones de recurrencia

***

# Concepto

Se puede entender una **relación de recurrencia (RR)**, como aquel objeto o función que contenga en su interior una copia de sí mismo. Se dice que esa función es recurrente al presentar esa propiedad. Por ejemplo:

```python
def factorial(n) :
    if n == 1 :
        return 1
    else :
        return (n * factorial(n - 1))
```

La función anterior (`factorial()`), es recursiva, ya que en su interior posee una llamada a sí misma.

## Orden de recurrencia

El **orden de recurrencia** es igual a la cantidad total de llamadas que una función se hace a sí misma, `factorial()` es una **RR de orden uno**, en cambio la siguiente función es una **RR de orden dos**:

> f<sub>n</sub> = f<sub>n - 1</sub> + f<sub>n - 2</sub>

A un mayor **orden de recursión** se complica determinar su **orden de crecimiento** así como eliminar la recursión de esa función / algoritmo.

## Inconveniente

La **recurrencia** en un código puede consumir demasiados recursos, y ser ineficiente, por lo que se trata de pasar de un **modelo recurrente** a uno **iterativo**, **resolviendo la RR**.

## Caso base

Se dice **caso base** a aquel momento donde la función no presenta más recurrencia, es decir el caso base es aquel donde la función no se llama más a sí misma. Por ejemplo en `factorial()`, el caso base es cuando `n` es igual a `1`.

# Resolviendo una RR

## Sustitución hacia atrás

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

De la misma manera que con la sustitución hacia atrás, se puede obtener del proceso anterior una manera de resolver la RR. Sin embargo, la **implementación iterativa no usa recursión**, por lo que necesita de un análisis más profundo del ejercicio. De la siguiente manera:

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

***

## Noción de un árbol

Para comprender la complejidad de un algoritmo, se puede observar la profundidad que alcanza el árbol de llamadas recursivas.

Un árbol es una estructura de datos que representa los subproblemas que un problema `n` debe resolver, de la siguiente manera:

<center><img src="/eif203/images/arbol.svg" width="400"/></center>

En algún momento el árbol llegará a los casos base, y la cantidad de **nodos** (esferas en el diagrama) será un indicador de la complejidad de este. Los **nodos** se unen por enlaces llamados **arcos**. 

[Definición formal de árbol (próximanente)]()

***

## DyC (divide y conquista)

Consiste en dividir un problema en varios de menor tamaño, con la finalidad de que resolviendo esos subproblemas se puede resolver el problema principal.

### Ejemplo de búsqueda binaria

Dada la lista `a = [10, 15, 21, 25, 35, 40, 45]`, ordenada y con elementos no repetidos, se busca `x = 19`.

| **0** | **1** | **2** | **3** | **4** | **5** | **6** |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
|   10  |   15  |   21  |   25  |   35  |   40  |   45  |

Se parte del punto medio y se evalúa si este es mayor o menor a `x`, de ahí se toma la decisión de buscar en el lado de la lista donde `x` posiblemente esté.

> Punto medio es 25, y 19 es menor que 25, por lo que se busca al lado **izquierdo** de la lista.

| **0** | **1** | **2** |
|:-----:|:-----:|:-----:|
|   10  |   15  |   21  |

> Punto medio es 15, y 19 es mayor que 15, por lo que se busca al lado **derecho** de la lista.

| **2** |
|:-----:|
|   21  |

> 21 es distinto de 19, por lo que este no existe en la lista y se retorna -1.

#### Programación en Python

```python
def busbin(x:int, a:list) : 
    def buscando(left, right) :
        if left > right :
           return -1 # No encontrado
        m = (right + left) // 2 # Punto medio
        if x == a[m] :
            return m # Encontrado
        if x < a[m] :
            return buscando(left, m - 1)
            # Buscando al lado izquierdo
        return(m + 1, right) # Omite preguntar x > a[m]
        # Buscando al lado derecho
    return buscando(0, len(a) - 1)

x = 19
a = [10, 15, 21, 25, 35, 40, 45]
print(busbin(x, a))
# Salida: -1
```

#### Tiempo de corrida de busbin(...)
1. El tamaño de los datos es `len(a)`
2. Operaciones (comparaciones entre `x` y elementos de la lista):
   1. T<sub>==</sub> = T<sub> < </sub> = O(1)
3. Relación de recurrencia:
   1. T<sub>busbin</sub>(n) = T<sub>buscando</sub>(n)
   2. El tiempo de T<sub>buscando</sub>(n) se determina según:

<center><img src="/eif203/images/whboard.png" width=""/></center>

{:start="4"}
4. Teorema de MT (Master theorem, pendiente)
5. Teorema de MT (Master theorem, pendiente)
   1. T<sub>buscando</sub>(n) ~ O(log(n))

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**
