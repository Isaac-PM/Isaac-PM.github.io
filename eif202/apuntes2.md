---
title: "Protección eléctrica de equipos y puertas lógicas"
author: "Isaac Palma Medina"
---
# Protección eléctrica de equipos y puertas lógicas

***

# Protección eléctrica

Al utilizar corriente alterna se deben prever determinados escenarios problemáticos para la salud del equipo (daño y envejecimiento prematuro), como lo son:

- Sobretensión (picos de voltaje)
- Baja tensión
- Corte de corriente
- Corriente con ruido/interferencias (electromagnéticas)

## Protectores de sobretensión

Su capacidad la indica el índice TVSS (supresor de sobretensiones de voltaje transitorias), el voltaje que debe pasar se tiene que considerar bajo, idealmente que no sobrepase los 400V. Es ideal que un protector de sobretensión incluya:

- Protección ante rayería
- Fusibles diseñados para una tensión extrema

## Unidades de respaldo con baterías (SAI o UPS)

Se distinguen diferentes características:

- Tiempos de funcionamiento (alimentación después del corte)
- Soporte de protección en la red
- Apagado automático
- Su capacidad puede ser medida en **voltiamperios (VA)**

Las características, fabricación e instalación de los SAI se rigen bajo las normas: UL-1499 e IEEE-578.

### Tipos de SAI

#### Verdaderos

Proporciona al equipo con energía exclusivamente de la batería, aislando a este de la red électrica.

#### En espera

Únicamente usa la batería cuando se corta el suministro électrico.

### Elección del SAI

Se utiliza una tabla donde se denota el consumo en watts (W) de cada compenente (o equipo), posteriormente se hace la conversión a VA, multiplicando la sumatoria de watts por 1,45; por ejemplo:

|   **Equipo a proteger**   | **Consumo en W** |
|:-------------------------:|:----------------:|
| Monitor led               |        78        |
| Computadora de escritorio |        240       |
| Enrutador                 |        60        |
| Impresora                 |        150       |
| Total                     |       528W       |

**Conversión a VA:** 528W * 1,45 = 765,60VA

**Multiplicación por el factor de crecimiento o resguardo:** 765,60VA * 1,25 = 957VA.

**Conclusión:** 957VA debería ser el valor ideal del SAI para los equipos dados.

## Reguladores de voltaje

Los reguladores de voltaje colaboran a compensar las diferencias existentes en el voltaje de las redes eléctricas, ayudan a que la salida de energía se mantenga entre los **120V o 240V**.

## Resolución de problemas relacionados a la CA en un equipo de cómputo

1. Comprobar que el equipo se encuentra conectado a la red électrica.
2. Asegurarse que el selector de voltaje de la fuente de poder coincide con el del sistema eléctrico (en Costa Rica 120V).
3. Comprobar la conexión del teclado.
4. Abrir el _case_ del equipo y asegurarse que no haya componentes o tornillos sueltos.
5. Verificar la conexión del cable de 24 pines en la tarjeta madre.
6. Buscar fusibles.
7. Quitar las tarjetas de expansión y las conexiones a unidades de almacenamiento, posteriormente revisar los puertos con un multímetro.
8. Reinstalar las tarjetas de expansión una a la vez.
9. Aquella tarjeta en mal funcionamiento hará que el equipo se detenga.
10. Comprobar la línea Power Good con un multímetro.

# Compuertas lógicas




![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/index)**