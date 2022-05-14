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

Sea R una relación sobre A,B: xRy ≡ x ∈ A es par, y ∈ B es 'a' ó 'c'

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

**x** issubclass **y** sii x = y ó x hereda de y

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

***

## Relaciones de equivalencia

**Clase de equivalencia**, son aquellos elementos equivalentes en una relación. Es **reflexiva**, **simétrica** y **transitiva**.

<center><img src="/eif203/images/equivalencia.jpg" width=""/></center>

[x]<sub>R</sub> = {y / xRy}, se refiere a un "representante" que es equivalente a los otros del "conjunto".

### Propiedades clases de equivalencia

Sea R una relación de equivalencia sobre A != 0:

- Todo x en A pertenece al menos a una clase de equivalencia (consigo misma): xRx ∀ x de manera que: [x]<sub>R</sub> = {y / xRy} → x ∈ [x]<sub>R</sub>
- Todo x en A pertenece a lo mas en una clase de equivalencia. Debido a transitividad, todos los elementos se relacionan entre sí, dando lugar a una sola clase.
- El unir todas las clases de equivalencia da lugar a A

#### Ejemplo de clausuras

A = {a, b, c, d, e}

R = {(a,b), (e,b), (d,c), (d,f)}

<center><img src="/eif203/images/ejemplo1.jpg" width=""/></center>

> Añada las relaciones mínimas necesarias para que R sea reflexiva (clausura reflexiva).

<center><img src="/eif203/images/ejemplo2.jpg" width=""/></center>

> Añada las relaciones mínimas necesarias para que R sea simétrica (clausura simétrica).

<center><img src="/eif203/images/ejemplo3.jpg" width=""/></center>

> Añada las relaciones mínimas necesarias para que R sea transitiva (clausura transitiva).

<center><img src="/eif203/images/ejemplo4.jpg" width=""/></center>

Además se deben añadir nuevos arcos (en verde) para mantener la simetría de las relaciones.

***

### Metodología de resolución

<center><img src="/eif203/images/resolucion.jpg" width=""/></center>

### Ejercicio de ejemplo 1

Dado un conjunto A, y una relación R **sobre** A (A→A, A relacionado con A), tal que R ⊆ AxA. R siendo de equivalencia.

#### ¿Relación de equivalencia no vacía más pequeña posible?

<center><img src="/eif203/images/identii.jpg" width=""/></center>

Se conoce como relación identidad ya que cumple con las tres condiciones siendo las más pequeña.

### Ejercicio de ejemplo 2

Sean R1 y R2 dos relaciones sobre un conjunto A.

#### ¿Si R1 y R2 son reflexivas (hipótesis) entonces la unión lo es?

R1∪R2 = {(x,y) / (x,y) ∈ R1 ó (x,y) ∈ R2}

R1∪R2 = {(x,y) / xR1y ó xR2y}

> Hay que probar: x(R1∪R2)x, es verdadero

> Es equivalente a: (x,x) ∈ R1∪R2

> sii (x,x) ∈ R1 ó (x,x) ∈ R2 (con que una se cumpla es verdadero)

> Es verdadero debido a que R1 y R2 son reflexivas (según hipótesis)

***

# Operaciones 

***

Sea A un conjunto y R1 y R2 relaciones sobre A.

### Ejemplo

**A: personas**

**R1: esAmigoDe**

**R2: estudiaCon**

**p** y **q** son personas en **A**:


## Unión ∪

> R1∪R2 = {(x,y) / xR1y ó xR2y}

> x(R1∪R2)y sii xR1y ó xR2y

Entonces si **p** y **q** son personas en **A**:

> p(R1∪R2)q sii pR1q ó pR2q

> R1∪R2: esAmigoDe ó estudiaCon

> p(R1∪R2)q: p esAmigoDe q ó p estudiaCon q

## Intersección ∩

> R1∩R2 = {(x,y) / xR1y y xR2y}

> x(R1∩R2)y sii xR1y y xR2y

> R1∩R2: esAmigoDe y estudiaCon

> p(R1∩R2)q: p esAmigoDe q y p estudiaCon q

## Inversa R<sup>-1</sup>

Sea R sobre A: R<sup>-1</sup> = {(y,x) / xRy}

## Ejemplo

A = {a, b, c, d}

R1 = {(a,a), (a,c), (b,c), (c,b)}

R2 = {(b,b), (b,c), (c,a)}

### Calcule

R1∪R2 = {(a,a), (a,c), (b,c), (c,b), (b,b), (c,a)}

R1∩R2 = {(b,c)}

R1<sup>-1</sup> = {(a,a), (c,a), (c,b), (b,c)}

R2<sup>-1</sup> = {(b,b), (c,b), (a,c)}

**Matriz de R1**

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   1   |   0   |   1   |   0   |
| **b** |   0   |   0   |   1   |   0   |
| **c** |   0   |   1   |   0   |   0   |
| **d** |   0   |   0   |   0   |   0   |

**Matriz de R2**

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   0   |   0   |   0   |   0   |
| **b** |   0   |   1   |   1   |   0   |
| **c** |   1   |   0   |   0   |   0   |
| **d** |   0   |   0   |   0   |   0   |

**Matriz de R1∪R2**

Se hace uso de una conjunción lógica por cada entrada.

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   1   |   0   |   1   |   0   |
| **b** |   0   |   1   |   1   |   0   |
| **c** |   1   |   1   |   0   |   0   |
| **d** |   0   |   0   |   0   |   0   |

**Matriz de R1∩R2**

Se hace uso de una disyunción lógica por cada entrada.

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   0   |   0   |   0   |   0   |
| **b** |   0   |   0   |   1   |   0   |
| **c** |   0   |   0   |   0   |   0   |
| **d** |   0   |   0   |   0   |   0   |

**Matriz de R1<sup>-1</sup>**

Matriz transpuesta.

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   1   |   0   |   0   |   0   |
| **b** |   0   |   0   |   1   |   0   |
| **c** |   1   |   1   |   0   |   0   |
| **d** |   0   |   0   |   0   |   0   |

### Implementación en Python

```python
import numpy as np

LR1 = [[1, 0, 1, 0], [0, 0, 1, 0], [0, 1, 0, 0], [0, 0, 0,0]]

LR1 = [[0, 0, 0, 0], [0, 1, 1, 0], [1, 0, 0, 0], [0, 0, 0,0]]

MR1 = np.matrix(LR1)

MR2 = np.matrix(LR2)

MR1uMR2 = MR1 | MR2 # Unión.

MR1yMR2 =  MR1 & MR2 # Intersección.

MR1porMR2 = MR1 @ MR2 # Producto punto.

MR1T= MR1.transpose() # Transpuesta.
```
***

## Composición

Sea R1 sobre A → (en) B

Sea R2 sobre B → C

(Se necesita el B en común)

x(R1·R2)y sii ∃ z / xR1z y zR2y

<center><img src="/eif203/images/compo.jpg" width=""/></center>

### Ejemplo

A: personas = {Juan, María, ...}

B: videojuegos = {fifa2022, mario, ...}

C: precios = {$50, $20, $100, ...}

R1: compra

R2: vale

> Juan compra fifa2022

> fifa2022 vale 20, 50, 100

> R1·R2 → Juan(compra·vale)y sii ∃ z / Juan compra un z y un z vale y → Juan compra un videojuego y un videojuego vale 20

<center><img src="/eif203/images/juan.jpg" width=""/></center>

```python
"""
La composición en Python se denota como el producto punto.
"""
MR1oMR2 = MR1 @ MR2 
```
Sea la siguiente matriz el resultado de MR1·MR2

| **-** | **a** | **b** | **c** | **d** |
|:-----:|:-----:|:-----:|:-----:|:-----:|
| **a** |   1   |   0   |   0   |   0   |
| **b** |   1   |   0   |   0   |   0   |
| **c** |   0   |   1   |   1   |   0   |
| **d** |   0   |   0   |   0   |   0   |

<center><img src="/eif203/images/matr.jpg" width=""/></center>

Los números indican la cantidad de "caminos" que existen para llegar a un dato.

### Ejemplo

<center><img src="/eif203/images/matr.jpg" width=""/></center>

## Composición múltiple

<center><img src="/eif203/images/rmul.jpg" width=""/></center>

<iframe src="https://trinket.io/embed/python/edd948bf08" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**