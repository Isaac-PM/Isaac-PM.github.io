---
title: "Tarjetas madre"
author: "Isaac Palma Medina"
---
# Tarjetas madre

***

# Generalidades sobre las tarjetas madre (mobo)

Su función principal es **interconectar los componentes de la computadora** por medio de circuitos impresos, conjugando:

- RAM y ROM
- Procesador (CPU)
- Tarjetas de audio, video y red
- Dispositivos de entrada y de salida (I/O)

## Factores de forma

El factor de forma determina y estandariza las dimensiones, lugar de conectores y puertos I/O, y se dividen en los siguientes estándares (de mayor a menor en tamaño):

- ATX
- microATX
- miniATX
- flexATX

[Ver tabla completa.](https://youtu.be/Ao7xDX8g9tw?t=686)

# Bus del sistema

Se entiende como el circuito que permite la transferencia de datos, compuesto por pistas metálicas por donde circulan señales que corresponden a los datos binarios del lenguaje máquina.

## Tipos de buses según el método de envío

### Bus serial

Los datos son enviados bit a bit, y son reconstruidos por medio de software, es usado en (mayor esfuerzo para una tarea):

- Unidades de almacenamiento
- Tarjetas de expansión
- Bus del CPU
- USB y Thunderbolt

### Bus paralelo

Los datos son enviados en bytes (8 bits) de manera simultánea, en varias líneas, es usado en:

- Unidades de almacenamiento
- CPU
- Tarjetas de video
- Impresoras

## Tipos de buses por su uso (tipos de datos)

### Bus de control

Controla el acceso a las líneas de dirección y datos, permite que no haya choque de información en el sistema. Tiene un rol administrativo que controla las operaciones del sistema por medio del reloj interno del CPU.

### Bus de dirección

Se entiende como un conjunto de líneas eléctricas que permiten el establecimiento de una dirección. Es unidireccional, definiendo la dirección de memoria de la información que se está transmitiendo.

### Bus de datos

Mueve los datos entre los dispositivos de hardware (I/O) y los dispositivos de almacenamiento.

# Puertos de entrada y salida (I/O ó E/S) integrados

<center><img src="/eif202/images/puertos.jpg" width=""/></center>

## Blindaje EMC

Los puertos generalmente contienen **"EMC Shielding"**, lo cual se refiere a cualquier método utilizado para proteger una señal sensible de señales electromagnéticas externas, o para evitar que una señal más fuerte se filtre e interfiera con los componentes electrónicos circundantes.

# Ranuras de memoria

## Ranuras de memoria RAM

Pueden ser cuatro o dos, vienen en pares con códigos de colores.

# Ranuras de expansión

## Ranuras PCI

Usan un bus serial "punto a punto", denominada **enlace**. Se pueden conectar tarjetas de:

- Red
- Audio
- Video
- E/S
- Adaptadores para dispositivos de almacenamiento

## Ranuras PCIE

Presentan un mayor ancho de banda (E = express), se definen según su número de _lanes_:

- x1
- x4
- x8
- x16

# Interfaces de almacenamiento

| **Interfaz** |  **Velocidad** |            **Usos sugeridos**           |
|:------------:|:--------------:|:---------------------------------------:|
|  SATA GEN.1  |    1,5 Gb/s    |        Disco duro, grabadora DVD        |
|  SATA GEN.2  |    3,0 Gb/s    |        Disco duro, grabadora DVD        |
|   PATA/IDE   | 1,0 - 1,3 Gb/s | Disco duro, grabadora DVD, grabadora CD |
|     SCSI     | 1,6 - 3,2 Gb/s |   Disco duro, almacenamiento en cinta   |

## SATA

Se pueden encontrar de 2 hasta 8 en una tarjeta madre.

## SCSI

Diseñado para ordenadores de bajo perfil.

# Zócalo

Es el **"puerto"** donde se conecta el procesador, se hace por medio de un sistema de varios **pines (ZIF)**, que varían de fabricante a fabricante.

# Chipset

Es el conjunto de chips (o circuitos integrados) en la placa madre cuya función es el control de los buses, interfaz I/O y USB, señales de interrupción IRQ y DMA, entre otras. Se encarga de entablar la conexión correcta entre la placa madre y diversos componentes esenciales de la PC.

## Arquitectura tradicional

### North bridge o puente norte

- Se considera un componente de suma importancia
- Controla funciones de acceso desde y hasta:
  - CPU
  - Ranuras de expansión
  - RAM
  - APU
  - South bridge (puente sur)
- Visualmente es el segundo chip más grande despdespués ues del CPU

### South bridge o puente sur

- Comunica al con los periféricos  conectados
- Se conoce como ICH (Input / Output Controller Hub)

# Procesador (CPU)

Compuesto por:

- Unidad de control
  - Controla el flujo de información
- Unidad aritmético lógica
  - Efectúa cálculos aritméticos y lógicos
  - Usa elementos llamados transistores

# BIOS

Se entiende como el sistema básico de entrada y salida, viene incorporado directamente en la mobo a través de memoria flash. Se encarga de la configuración de la placa base y de sus componentes.

Se ejecuta al inicio del equipo, y se verifica el funcionamiento de todos los componentes, por medio del **POST (Power On Self Test)**, se autocomprueba:

- CPU
- Memoria
- Chipset
- Unidades de almacenamiento
- Periféricos  cruciales

Si el **POST** detecta un error, el equipo podría mostrar un código de error o una serie de bips.

Se accede por medio de distintas teclas.

# UEFI

Tiene el mismo objetivo que la BIOS, sin embargo, posee una interfaz gráfica más amigable y un gran soporte para el uso con mouse, además de distintas herramientas de recuperación, OC, diagnóstico. Además, permite la instalación de dispositivos con mucha más capacidad. 

# Batería

Es una batería de tipo pastilla modelo **CR2032**, ayuda en la persistencia de la fecha, hora y configuraciones de esta. Su duración es de varios años.

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif202/portadaeif202)**