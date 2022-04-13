---
title: "Protección eléctrica de equipos y puertas lógicas"
author: "Isaac Palma Medina"
---
# Protección eléctrica de equipos y puertas lógicas

***

## Protección eléctrica de equipos de cómputo

Al utilizar corriente alterna se deben preveer determinados escenarios problemáticos para la salud del equipo (daño y envejecimiento prematuro), como lo son:

- Sobretensión (picos de voltaje)
- Baja tensión
- Corte de corriente
- Corriente con ruido/interferencias (electromagnéticas)

### Protectores de sobretensión

Su capacidad la indica el índice TVSS (supresor de sobretensiones de voltaje transitorias), el voltaje que debe pasar se tiene que considerar bajo, idealmente que no sobrepase los 400V. Es ideal que un protector de sobretensión incluya:

- Protección ante rayería
- Fusibles diseñados para una tensión extrema

### Unidades de respaldo con baterías (SAI o UPS)

Se distinguen diferentes características:

- Tiempos de funcionamiento (alimentación después del corte)
- Soporte de protección en la red
- Apagado automático
- Su capacidad puede ser medida en **voltiamperios (VA)**

Las características, fabricación e instalación de los SAI se rigen bajo las normas: UL-1499 e IEEE-578.

#### Tipos de SAI

##### Verdaderos

Proporciona al equipo con energía exclusivamente de la batería, aislando a este de la red électrica.

##### En espera

Únicamente usa la batería cuando se corta el suministro électrico.

#### Elección del SAI

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








**[¡Regrésame!](/index)**