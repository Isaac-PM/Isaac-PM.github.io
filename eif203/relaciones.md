---
title: "Relaciones binarias y diccionarios"
author: "Isaac Palma Medina"
---

# Relaciones binarias y diccionarios

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
# <class 'set'>

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


### Representación en matriz, M<sub>R</sub> (matriz de adyacencia)

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

R es transitiva: ∀ x,y,z : xRy ^ yRz → xRz

Los términos no necesariamente son diferentes.

<center><img src="/eif203/images/digrafotransitiva.jpg" width=""/></center>

### Equivalencia

Es reflexiva, simétrica y transitiva.

### Irreflexiva

∀ x : x¬Rx

Leído x NO está relacionado consigo mismo.

### Antisimétrica

∀ x,y : ∀ x,y : xRy ^ yRx → x = y

Leído x está relacionado con y, et y está relacionado con x, siendo x et y el mismo objeto.

***

## Análisis de un ejemplo

<center><img src="/eif203/images/digrafoejemplo.jpg" width=""/></center>

A = {a, b, c} (A es el **dominio**).

R = {(a,b), (b,a), (c,c)}

### ¿Es R reflexiva?

NO, **contrajemplo:** a no está relacionado consigo mismo.

```
Para c/x
    Si xRx
```

Lo anterior posee un tiempo de corrida ~O(n).

### ¿Es R simétrica?

Si, **prueba:** aRb y bRa, cRc y cRc

```
Para c/x
    Para c/y
    Si xRy entonces yRx
```

Lo anterior posee un tiempo de corrida ~O(n<sup>2</sup>).

### ¿Es R transitiva?

NO, **contrajemplo:** aRb y bRa pero a¬Ra

Tiempo de corrida ~O(n<sup>3</sup>).

### ¿Es R de equivalencia?

NO, ya que es únicamente simétrica.

### ¿Es R irreflexiva?

NO, **contrajemplo:** cRc.

```
Para c/x
    Si x¬Rx
```

Lo anterior posee un tiempo de corrida ~O(n).


### ¿Es R antisimétrica?

NO, **contrajemplo:** aRb y bRa pero a != b

Tiempo de corrida ~O(n<sup>2</sup>).

***

## Relación de orden parcial

Una relación de orden parcial es:

- reflexiva
- antisimétrica
- transitiva

### Ejemplo issubclass con clase Animal

```python
# Input
>>> issubclass(Dog, Animal)
# Output
>>> True

# Input
>>> issubclass(Dog, Dog) 
# Output
>>> True # es reflexiva

# Input
>>> issubclass(Animal, Dog) 
# Output
>>> False # es antisimétrica

# Input
>>> class Chihuahua(Dog): pass
>>> issubclass(Chihuahua, Animal) 
# Output
>>> True # es transitiva
```

<center><img src="/eif203/images/digrafois.jpg" width=""/></center>

***

## Diccionarios en Python

Hace uso de una función de hash, que convierta un objeto a un número, el cual sería el identificador del objeto en el diccionario.

```python
# Input
>>> dic = {'ab': 10, 'cd': 21, 'ef': 32, 'gh': 43, 'ij': 54} # Las letras entre comillas serían el identificador explícito.
>>> dic['ef'] # Llamar a un elemento
# Output
>>> 32

# Input
>>> dic['kl'] = 65 # Añadir un nuevo elemento

```

### Representación de un digrafo en un diccionario (lista de adyacencia)

<center><img src="/eif203/images/digrafo1.jpg" width=""/></center>

#### Representación en matriz

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   1   |   1   |   1   |   0   |
| **b** |   1   |   0   |   1   |   0   |
| **c** |   0   |   0   |   0   |   1   |
| **d** |   0   |   0   |   0   |   0   |

#### Representación en diccionario

```python
>>> dic = {'a':['a', 'b', 'c'], 'b':['a', 'c'], 'c':['d'], 'd':[]}
```

<iframe src="https://trinket.io/embed/python/edd948bf08" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**