---
title: "La alimentación del computador y demás componentes electrónicos"
author: "Isaac Palma Medina"
---
# La alimentación del computador y demás componentes electrónicos

***

# Fuentes de poder (PSU)

Está compuesta por una unidad que distribuye la energía a los distintos componentes, estos se ven conectados por medio de pines, que poseen cierta cantidad de pines.

**EL conector principal es aquel de 24 pines**

Por medio de los cables se entregan distintos voltajes, los cuales van desde los 3,3V, 5V y 12V, generalmente los 12V se utilizan para los motores de los componentes.

## Comprobar el funcionamiento de la fuente de poder

El ventilador de la PSU debería girar al realizar el puente entre los pines.

<center><img src="/eif202/images/puente.png" width="400"/></center>

Otro nombre válido para las fuentes de poder son los **transformadores**.

## Voltajes usados

|       **Componente**      | **Voltaje** |
|:-------------------------:|:-----------:|
|          RAM DDR3         |     1,5V    |
|          RAM DDR4         |     1,2V    |
|            CPU            |     1,5V    |
|       Tarjetas PCIe       |     3,3V    |
| ISA (ranura de expansión) |      5V     |

## Funciones principales de las PSU

### Transformación

El voltaje de la línea eléctrica se reduce al necesario por los componentes, aproximadamente de 120V a 12V-5V. Se usan **inductores bobinados**.

### Rectificación y filtrado

Se convierte la **corriente alterna a corriente continua**. Se logra gracias a componentes llamados **diodos** y un **condensador / capacitor**, configurados de tal manera que forman un **puente rectificador** (full bridge rectifier), que solo permite el paso de las ondas "positivas" del voltaje, y es sostenido en el pico de la onda (filtrado).

Se "suaviza" la CC y se le añade "calidad", por medio de **capacitores**.

### Regulación

Por medio de distintos componentes y **circuitos integrados**, la corriente es ajustada para las necesidades del aparato, obtiene finalmente su forma lineal y constante.

<center><img src="/eif202/images/rectificacion.jpg" width="400"/></center>

## Tipos de fuente de poder

### Fuentes AT

<center><img src="/eif202/images/at.jpg" width="400"/></center>

Las siglas tienen el significado de **Advanced Technology**, surge como un estándar por parte de IBM, consistiendo en una placa de unos 100mm. Comienza a ser descontinuado en los años 90.

#### Características

- 2 conectores de 6 pines
- Encendido y apagado manual mediante un botón
- Incorporación de cables FLOPPY
- No poseían cables diseñados para la alimentación de tarjetas gráficas o el procesador
- Menor eficiencia y seguridad
- - El voltaje suministrado no supera los 250W

### Fuentes ATX

<center><img src="/eif202/images/atx.jpg" width="600"/></center>

Las siglas significan **Advanced Technology Extended**, hace referencia a un **factor de forma** que determina yu estandariza las dimensiones, lugar de conectores y puertos I/O.

Surge como la **evolución de las fuentes AT**.

#### Características

- Suministra energía a toda la placa madre usando un conector de 24 pines.
- No requiere encendido o apagado manual (desconexión de la red eléctrica).
- Incorporan cables exclusivos para la alimentación del procesador (EPS) y de tarjetas gráficas.
- El voltaje suministrado puede superar los 300W
- Buena optimización del uso de la energía

### Clasificaciones de la fuente de poder (ATX)

#### Tipo

- **Modulares:** Permiten desconectar los cables directamente de la PSU, dejando únicamente los necesarios para el funcionamiento del equipo.
- **Semi-modulares:** Permiten desconectar ciertos cables directamente de la PSU, teniendo directamente incrustados los cables básicos, permitiendo desconectar cables opcionales.
- **No modular:** No permiten desconectar cables de la PSU.

#### Certificaciones

La clasificación de la calidad de las fuentes de poder es medida según la certificación 80 plus:

- 80 plus White: presentan una eficiencia máxima al 100% de su carga de 80% sobre la potencia total.
- 80 plus Bronze:  presentan una eficiencia máxima al 100% de su carga de 82% sobre la potencia total.
- 80 plus Silver: presentan una eficiencia máxima al 100% de su carga de 85% sobre la potencia total.
- 80 plus Gold: presentan una eficiencia máxima al 100% de su carga de 87% sobre la potencia total.
- 80 plus Platinum: presentan una eficiencia máxima al 100% de su carga de 97% sobre la potencia total.
- 80 plus Titanium: presentan una eficiencia máxima al 100% de su carga de 91% sobre la potencia total.

Si bien la eficiencia puede no escalar linealmente, la calidad de los componentes en cada _tier_ de la certificación mejora.

# Vatios, voltiamperios y factor de potencia

## Vatio

El vatio o watt (W), es la unidad usada para medir la **potencia**, es igual a un julio por segundo.

## Voltiamperio o voltaje electrotécnico

Es la unidad de medida de potencia en un sistema de corriente alterna.

## Factor de potencia

Es la relación entre la potencia activa (energía a aprovechar o útil) y la potencia aparente (energía perdida).

# Factor de forma de un computador

Son aquellas características que permiten la correcta integración física y eléctrica de un equipo.

**Un _form factor_, describe las siguientes características:**

- La forma de la placa base
- Dimensiones físicas de la placa base
- Posición de los anclajes (tornillos)
- Posición de las ranuras de expansión y puertos I/O
- Las conexiones eléctricas de la tarjeta: cantidad y tipo

# Mantenimiento

**[Ver video](https://www.youtube.com/watch?v=3ndtLucxA5E)**

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif202/portadaeif202)**