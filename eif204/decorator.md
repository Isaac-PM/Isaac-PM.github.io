---
title: "Análisis de un algoritmo"
author: "Karla Verónica Quirós"
---

# Patrón _decorator_

**Por: Karla Verónica Quirós**

***

## ¿Cuándo se debe aplicar?

> Para añadir funciones dinámicas a un objeto.

Esto nos permite no tener que crear sucesivas clases que hereden de la primera incorporando la nueva funcionalidad, sino otras que la implementan y se asocian a la primera.

### Ventajas del patrón decorador:

- Alto grado de flexibilidad 
 
- Ampliación de las funciones de las clases sin necesidad de usar herencia 

- Código de programa legible 

- Da funciones más optimizadas.

### Sobrecarga de operadores:

La sobrecarga de operadores brinda la opción de sumar tanto datos como objetos.

#### Ejemplo:

| **Operadores** |                    **Resultado**                   |
|:--------------:|:--------------------------------------------------:|
|      3 + 4     |                Retorna un entero = 7               |
|   per1 + per2  |      Retorna la suma de edades de dos personas     |
|  cont1 + cont2 | Retorna la suma de los valores de dos contenedores |

**Los operadores que se pueden sobrecargar:**

> ==, +, -  ,*, <,>, <=, >=, /, //, %

 > < <, >>, delete, [ ]
 
 #### Ejemplo sobrecarga de operadores
 
 ```cpp
class Pareja
{
private:
	int a, b;
public:
	Pareja();
	// constructor parametrizado 
	Pareja(const int,const int);
	// constructor copia crea un objeto identico al que entra por parametro que ya existe
	Pareja(const Pareja& obj);
    // para sobrecargar operadores se sigue el siguiente orden
    // tipo de retorno operator (operador a cargar) (const nombre-clase& nombre de la variable)
	Pareja& operator + (const Pareja& p2);
    // operador de asignacion
	Pareja& operator = (const Pareja& p2);
    // operador de igualdad
	bool operator ==(const Pareja& p2);
    // operador no miembro es decir externo, sobrecarga flujo de salida
	friend ostream& operator <<(ostream& sal, const Pareja&);
    
```

**Tomando en cuenta el desarrollo de los métodos, más importantes:

```cpp
Pareja& Pareja::operator+(const Pareja& p2)
{
	this->a += p2.a;
	this->b += p2.b;
	return *this; // puntero es igual a & y & = *
}
// para igualar un objeto a otro primero debe asegurarse que sean distintos
Pareja& Pareja::operator=(const Pareja& p2)
{
	if (this != &p2) {
		if (p2.a != 0) this->a = p2.a;
		if (p2.b != 0) this->b = p2.b;

	}
	return *this;

}
// para que dos objetos sean iguales deben tener todos sus atributos con mismo valor
bool Pareja::operator==(const Pareja& p2)
{
	return (this->a == p2.a && this->b == p2.b);
}
```

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif204/portadaeif204)**