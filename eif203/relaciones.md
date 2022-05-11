---
title: "Relaciones binarias"
author: "Isaac Palma Medina"
---

# Relaciones binarias

***

Dados los conjuntos **A** y **B**, **R** es una relación si **R ⊆ AxB** (producto cartesiano). Se trabaja el caso donde A = B.

**Producto cartesiano:** AxB = {(a,b) / a ∈ A ^ b ∈ B}.

> A = {1, 2, 3} ^  B = {'c', 'd'}

> AxB = {(1, 'c'), (1, 'd'), (2, 'c'), (2, 'd'), (3, 'c'), (3, 'd')}

> Una relación cualquiera sería: R = {(1, 'c'), (3, 'd')}, es decir un subconjunto de AxB, denotado **1R'c'** (1 está relacionado con c)

## Conjuntos en Python

```python
# Input
>>> S = {7, 3, 9, 5, 3, 1, 5, 1}
>>> type(S)
# Output
<class 'set'>

# Input
>>> S
# Output
>>> S = {1, 3, 5, 7, 9} # Se eliminan los duplicados y se les asigna un orden arbitrario. 
```

## Notación por extensión y comprensión

### Extensión

ℕ<sub><5</sub> = {0, 1, 2, 3, 4}

### Comprensión

ℕ<sub><5</sub> = {n / n ∈ ℕ ^ n < 5}, leído: todos los n tal que n es un número natural y es menor a cinco

## Comprensión en Python

```python
# Input
>>> A = list(range(10))
>>> A
# Output
>>> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

"""
Extraer los pares en , por comprensión:
Pares en A {n / n ∈ A ^ n es par}
"""
# Input
>>> ParesEnA = [n for n in A if n % 2 == 0]
# "for" es leído como "tal que"(/) e "in" como "pertenece"(∈)
>>> ParesEnA
# Output
[0, 2, 4, 6, 8]

# Producto cartesiano, input
>>> A = list(range(5))
>>> B = list('abc')
>>> AxB = [(a, b) for a in A for b in B]
>>> AxB
# Output
[(0, 'a'), (0, 'b'), (0, 'c'), (1, 'a'), (1, 'b'), (1, 'c'), (2, 'a'), (2, 'b'), (2, 'c'), (3, 'a'), (3, 'b'), (3, 'c'), (4, 'a'), (4, 'b'), (4, 'c')]
```

### Ejemplos

A = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

B = {'a', 'b', 'c'}

Sea R una relación sobre A,B: xRy ≡ x ∈ A es par, y ∈ B es 'a' || 'c'

#### Implementación en Python

```python
# Input
>>> A = list(range(10))
>>> B = list('abc')
>>> R = [(x, y) for x in A if x % 2 == 0 for y in B if y == 'a' or y == 'b']
>>> R
# Output
[(0, 'a'), (0, 'b'), (2, 'a'), (2, 'b'), (4, 'a'), (4, 'b'), (6, 'a'), (6, 'b'), (8, 'a'), (8, 'b')]
```

## Representaciones de una relación (binarias)

A = {0, 1, 2}

B = {Juan, Ana, Pedro}

R = {(0, Juan), (0, Pedro), (1, Ana), (2, Pedro), (2, Juan)}


### Representación en matriz, M<sub>R</sub>

|   -   | **Juan** | **Ana** | **Pedro** |
|:-----:|:--------:|:-------:|:---------:|
| **0** |     1    |    0    |     1     |
| **1** |     0    |    1    |     0     |
| **2** |     1    |    0    |     1     |

> Se coloca un 1 en aquellos espacios que satisfacen la relación.

### Representación en un digrafo, G<sub>R</sub>

<center><img src="/eif203/images/digrafo.jpg" width=""/></center>

## Relación issubclass

**x** issubclass **y** sii x = y || x hereda de y

### Ejemplo con clase Animal

```python
# Input
>>> issubclass(Dog, Animal)
# Output
>>> True

# Input
>>> issubclass(Animal, Dog)
# Output
>>> False

# Input
>>> issubclass(Dog, Dog) # Se entiende como un arco que apunta hacia su origen, denominado en el digrafo un lazo
# Output
>>> True
```

## Propiedades de las relaciones

### Reflexiva

R es reflexiva: ∀ x : xRx

Leído x está relacionado consigo mismo.

> issubclass es reflexiva

#### Ejemplo

A = {a, b, c}

R es reflexiva. **¿Cómo sería la matriz?**

| **-** | **a** | **b** | **c** |
|:-----:|:-----:|:-----:|:-----:|
| **a** |   1   |   0   |   0   |
| **b** |   0   |   1   |   0   |
| **c** |   0   |   0   |   1   |

**¿Cómo sería el digrafo?**

<center><img src="/eif203/images/digraforeflexiva.jpg" width=""/></center>

### Simétrica

R es simétrica: ∀ x,y : xRy → yRx

<center><img src="/eif203/images/digrafosimetrica.jpg" width=""/></center>

### Transitiva

R es transivica: ∀ x,y,z : xRy ^ yRz → xRz

<center><img src="/eif203/images/digrafotransitiva.jpg" width=""/></center>
















<iframe src="https://trinket.io/embed/python/edd948bf08" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**