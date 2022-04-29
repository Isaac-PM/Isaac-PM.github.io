---
title: "DyC y MT, resolución RR"
author: "Isaac Palma Medina"
---

# DyC y MT, resolución RR

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