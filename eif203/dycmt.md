---
title: "Hanoi, DyC y MT, resolución RR"
author: "Isaac Palma Medina"
---

# Hanoi, DyC y MT, resolución RR

***

# Noción de un árbol

Para comprender la complejidad de un algoritmo, se puede observar la profundidad que alcanza el árbol de llamadas recursivas.

Un árbol es una estructura de datos que representa los subproblemas que un problema `n` debe resolver, de la siguiente manera:

<center><img src="/eif203/images/arbol.svg" width="400"/></center>

En algún momento el árbol llegará a los casos base, y la cantidad de **nodos** (esferas en el diagrama) será un indicador de la complejidad del algoritmo. Los **nodos** se unen por enlaces llamados **arcos**, el nodo del que nace el árbol se le denomina **root** o **raíz**.

[Definición formal de árbol (próximanente)]()

## Ejemplo de un árbol, caso Hanoi

Se requiere mover cierta cantidad de discos de una posición A a una posición C, siguiendo los siguientes lineamientos:

- Mover un disco a la vez
- Mover únicamente el disco de más arriba
- Únicamente colocar discos pequeños sobre discos grandes

<center><img src="https://upload.wikimedia.org/wikipedia/commons/6/60/Tower_of_Hanoi_4.gif?20050322192703" width=""/></center>

By André Karwath aka Aka - Own work, CC BY-SA 2.5, https://commons.wikimedia.org/w/index.php?curid=85401

### Probar el juego

[Jugar aquí](/eif203/hanoi.html){:target="\_blank"}

<sub><sup>CC BY © 2015-2021 Trinket</sup></sub>

### Desarrollo de Hanoi

Sean A, B y C las posiciones en las que se deben colocar los discos, con el objetivo de mover los discos que se encuentran en A hacia C.

#### Árbol de llamadas

<center><img src="/eif203/images/arbolhanoi.jpg" width=""/></center>

#### Código de ejemplo

```python
def hanoi(n, A = "A", B = "B", C = "C") :
    if n == 1 :
        print(f"Mueve de {A} a {C}")
    hanoi(n - 1, A, C, B)
    print(f"Mueve de {A} a {C}")
    hanoi(n - 1, B, A, C)
```

#### Tiempo de Hanoi

##### Tamaño de los datos

El tamaño de los datos es igual a n (cantidad de discos)

##### Operación de interés

La operación de interes son: `print`

##### Ecuación de RR

<center><img src="/eif203/images/tiempohanoi.jpg" width=""/></center>

##### Resolución por sustitución hacia atrás

| **n** |        **A**       | **B** | **C = A + B** |
|:-----:|:------------------:|:-----:|:-------------:|
|   -   | 2T<sub>n - 1</sub> |   1   | T<sub>n</sub> |
|   1   |   2T<sub>1</sub>   |   1   |       1       |
|   2   |   2T<sub>2</sub>   |   1   |       3       |
|   3   |   2T<sub>3</sub>   |   1   |       7       |
|   4   |   2T<sub>4</sub>   |   1   |       15      |
|   5   |   2T<sub>5</sub>   |   1   |       31      |

##### Solución de la ecuación

> 1, 3, 7, 15, 31

> Diferencia entre los términos: 2, 4, 8, 16

Se observa que se trata de una sucesión que incrementa en 2<sup>n</sup> - 1, por lo que:

> **T<sub>hanoi</sub> = 2<sup>n</sup> - 1**

##### Orden de crecimiento

> **T<sub>hanoi</sub> ~ O(2<sup>n</sup>)**

***

# DyC (divide y conquista)

Consiste en dividir un problema en varios problemas de menor tamaño, con la finalidad de que, resolviendo esos subproblemas se puede resolver el problema principal.

## Búsqueda binaria

### Programado en en Python

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

### Árbol de llamadas

El árbol de llamadas de `busbin()` se hace siguiendo el algoritmo anterior, se muestran algunas partes del árbol que no se generan, con fines ilustrativos.

<center><img src="/eif203/images/arbolbusbin.jpg" width=""/></center>

Nótese que el último nodo, al no coincidir el elemento con el buscado devuelve -1, respuesta que se transporta hasta la raíz del árbol. Además se destaca la manera en la que se soluciona el problema por medio de la subdivisión en problemas de un orden más sencillo.

#### Árbol real

<center><img src="/eif203/images/arbolbusbinreal.jpg" width=""/></center>

El árbol real de `busbin()` no toma en cuenta aquellos casos donde `x` no pertenezca en el conjunto (siendo menor o mayor al punto medio de la lista).

### Paso a paso

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

# Master theorem (MT)

## Simple

Sea **a** igual al **número de llamadas recursivas**, sea **c** una constante referente al tiempo que toma **"obtener" la respuesta del nodo anterior** igual a **~ O(1)**, sea **b** el **divisor de n**. 

> a debe: a >= 1, a ∈ N y b debe: b > 1

> Si a > 1, entonces f<sub>n</sub> ~ O(n<sup>log<sub>b</sub>(a)</sup>)

> Si a = 1, entonces f<sub>n</sub> ~ O(log<sub>b</sub>(n))

> f<sub>n</sub> = a * f<sub>n / 2</sub> + c

### Árbol de una MT simple

<center><img src="/eif203/images/mtsimple.jpg" width=""/></center>

## General

Sea **a** igual al **número de llamadas recursivas**, sea **c** una constante referente al tiempo que toma **"obtener" la respuesta del nodo anterior** igual a **~ O(1)**, sea **b**. 

> a debe: a >= 1, a ∈ N y b debe: b > 1

> n es una potencia de b: n = b<sup>k</sup>

> Si a < b<sup>d</sup>, fn ~ O(n<sup>d</sup>)

> Si a = b<sup>d</sup>, fn ~ O(n<sup>d</sup> * log<sub>b</sub>(n))

> Si a > b<sup>d</sup>, fn ~ O(n<sup>log<sub>b</sub>(a)</sup>)

> f<sub>n</sub> = a * f<sub>n / b</sub> + c * n<sup>d</sup>

> Tiempo de combinar las soluciones: c * n<sup>d</sup>

### Árbol de una MT general

<center><img src="/eif203/images/mtgeneral.jpg" width=""/></center>

***

### Tiempo de busbin
1. El tamaño de los datos es `len(a)`
2. Operaciones (comparaciones entre `x` y elementos de la lista):
   1. T<sub>==</sub> = T<sub> < </sub> = O(1)
3. Relación de recurrencia:
   1. T<sub>busbin</sub>(n) = T<sub>buscando</sub>(n)
   2. El tiempo de T<sub>buscando</sub>(n) se determina según:

<center><img src="/eif203/images/whboard.png" width=""/></center>

{:start="4"}
4. Resolución de la RR
   1. <center><img src="/eif203/images/arbolbusbinmt.jpg" width=""/></center>
   2. Se puede observar que **a** es igual a 1 (solo se hace una llamada recursiva [solo se construye un arco]), **b** es igual a 2. **c** es igual a 1 (debido a que retorna -1 en un tiempo constante).
5. Orden de crecimiento
   1. Debido a su orden de crecimiento se puede inferir que su respuesta puede ser obtenida por medio del MT Simple.
   2. **a** es igual a 1, lo que implica que T<sub>buscando</sub>(n) ~ O(log(n))

## Mergesort

### Árbol de mergesort

<center><img src="/eif203/images/arbolmerge.jpg" width=""/></center>

### Algoritmo de merge

```python
def merge(a, b) :
    n, m = len(a), len(b) # Tamaño de ambas listas.
    i, j, k = 0, 0, 0
    result = [0] * (n + m) # Se crea una lista del tamaño final.
    while i < n and j < m :
        if a[i] < b[j] : # Compara e ingresa en la lista final los índices a[i] < b[j].
            result[k] = a[i]
            i += 1
        else : # Si b[j] < a[i].
            result[k] = b[j]
            j += 1
        k += 1
    while i < n : # Completar de recorrer la lista, una no quedó vacía.
        result[k] = a[i]
        i += 1
        k += 1
    while j < m :  # Completar de recorrer la lista, una no quedó vacía.
        result[k] = b[j]
        j += 1
        k += 1
    return result
```

### Algoritmo de mergesort

```python
def mergesort(a) :
    n = len(a)
    if n <= 1 :
        return a
    m  = n // 2
    return merge( mergesort(a[:m]), mergesort(a[m:]) )
```

### Tiempo de mergesort
1. Tamaño de los datos: cantidad de elementos en la lista
2. Operación de interés: comparación
3. Relación de recurrencia:
   1. <center><img src="/eif203/images/tiempoms.jpg" width=""/></center>
4. Orden de crecimiento según **MT**:
   1. <center><img src="/eif203/images/tiempoms.jpg" width=""/></center>
   2. T<sub>ms</sub> ~ O(nlog(n))

## Algoritmo máximo de una lista

<center><img src="/eif203/images/arbolmax.jpg" width=""/></center>

### Tiempo de de max según MT



<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**