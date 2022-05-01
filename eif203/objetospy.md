---
title: "Orientación a objetos en Python"
author: "Isaac Palma Medina"
---

# Orientación a objetos en Python

***

```python
class ObjetoFoo :
    # La palabra self es usada para instanciar
    # Todo por defecto es público

    # Funciona como un método constructor
    def __init__(self, atributo_1:Tipo) :
        self.atributo_1 = atributo_1

    # Los métodos especiales (__Foo__) se denominan dunder (double underscore)
    
    # Funciona como un método to_string()
    def __repr__(self) : # Siempre ingresar self
        return f"ObjetoFoo(atributo_1='{self.atributo_1}')"

    # Método de lógica de negocios
    def salute(self, human_name) :
        print(f"Hello, {human_name}...")

class ObjetoFooBar(ObjetoFoo) : # Herencia de ObjetoFoo
    def __repr__(self) : # Redefinición del método
        return f"ObjetoFooBar(atributo_1='{self.atributo_1}')"

    def bye(self, human_name) :
        print(f"Bye, {human_name}...")

objeto1 = ObjetoFoo('foobar1')

objeto2 = ObjetoFooBar('foobar2')
```

> La clase **ObjetoFooBar** **inherits** from **ObjetoFoo**, y **objeto2** is an instance de **ObjetoFooBar**, además **objeto2** is an instance de **ObjetoFoo**.

<center><sub><sup>Derechos reservados a los propietarios de las imágenes, enlace disponible en estas.</sup></sub></center>

![](https://img.shields.io/badge/License-CC\_BY--SA\_4.0-lightgrey.svg)

**[¡Regrésame!](/eif203/portadaeif203)**