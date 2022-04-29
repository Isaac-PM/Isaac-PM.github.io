---
title: "Pilas ó stacks"
author: "Isaac Palma Medina"
---

# Pilas ó stacks

Se entiende como pila ó stack a aquella **estructura de datos** que permite almacenar información siguiendo un patrón **Last In, First Out (LIFO)**, refiriéndose a que el último dato en ser ingresado al stack es el primero el ser eliminado.

A la acción de **ingresar** se le denomina **Push**, a la acción de eliminar se le llama **Pop**, a cada elemento del stack es referido como un **Frame**.

<center><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Lifo_stack.svg/800px-Lifo_stack.svg.png" width="400"/></center>

_By Vectorization: OmenBreeze - Own work based on: Lifo stack.png by Maxtremus, CC0, https://commons.wikimedia.org/w/index.php?curid=115938639_

## Uso para la visualización de una RR

Se conoce al **comportamiento de pila**, al uso de un stack para visualizar la manera en la que un algoritmo o función se comporta con determinada cantidad de datos.

### Ejemplo

```python
def exp(x, n) :
    if n == 0 :
        return 1
    return x * exp(x, n - 1)
```

### Comportamiento de pila en el caso `exp(2, 3)`

#### Primer push

<center><img src="https://i.imgur.com/2o2HdvU.png" width=""/></center>

En el primer **push**, se tienen los valores x = 2 y n = 3, mientras tanto el 2 se mantiene en espera del valor de la llamada recursiva, equivalente a la línea: `x * exp(x, n - 1)`. 

El resto de la construcción de la pila seguirá un comportamiento similar, el valor de x se mantiene constante mientras el **valor de n se reduce hasta legar al caso base**, donde n = 0.

#### Segundo push

<center><img src="https://i.imgur.com/MFrcdru.png" width=""/></center>

#### Tercer push

<center><img src="https://i.imgur.com/ZAHksRA.png" width=""/></center>

#### Cuarto push

<center><img src="https://i.imgur.com/VvnOMyE.png" width=""/></center>

Llegado al caso base, se detiene la construcción de la pila, el valor anterior de cada **frame** vendrá a sustituir al "?", eliminando cada frame anterior por medio de un **pop**.

#### Primer pop

<center><img src="https://i.imgur.com/BCUucID.png" width=""/></center>

#### Segundo pop

<center><img src="https://i.imgur.com/Nm0Rqfn.png" width=""/></center>

#### Tercer pop

<center><img src="https://i.imgur.com/2QC87kF.png" width=""/></center>

#### Cuarto pop

<center><img src="https://i.imgur.com/eXmOsU8.png" width=""/></center>

La respuesta es **8** y la pila creció **4 frames**, es decir la cantidad de frames en este caso es n + 1.

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**