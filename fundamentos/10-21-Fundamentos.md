# Día 6

Crear varios proyectos dentro de una solución en Visual Studio

Tipo valor vs referencia.

var, object, dynamic

## Módulo 7: estructuras, objetos y clases

* [Estructuras de datos simples](fundamentos/../10-18-Fundamentos.md#estructuras-de-datos)

* Estructuras de datos complejas:
  * Clases: de tipo referencia. Es una especia de plantilla en la que se deinen atributos (propiedades) y métodos de un objeto. A los objetos que se crean a partir de clases se los conoce como instancias de las mismas.
  A menudo es conveniente dar ciertos valores al instanciar una clase. Para esto se usa el constructor.
  Las clases pueden heredar los campos de otras clases o pueden implementar los campos que define una interfaz.
  * Estructuras *struct*: de tipo valor. Puede almacenar lo mismo que las clases. La mayor diferencia con respecto a las clases, aparte de que son de tipo valor frente a tipo referencia, es que no pueden heredar ni ser heredadas.

## Definiciones fundamentales POO

La programacion orientada a objetos es un paradigma cuyo propósito es organizar el código en función de quién y dónde se utiliza. Los elementos básicos del paradigma son los objetos, que se usan para definir un conjunto de miembros (propiedades, métodos, campos, etc.) que tienen relación entre ellos. Se basa en cuatro pilares:

* ***Herencia***: para evitar repetir código y que este sea más declarativo se pueden crear clases *base* de la que heredan las *subclases*.

* ***Encapsulación***: permite ocultar datos o métodos, modificar la información a la hora de mostrarla y validar los datos antes de guardarlos.

* ***Abstracción***:

* ***Polimorfismo***: una misma clase puede derivar en múltiples formas de la misma. Se relaciona fundamentalmente con las características anteriores.

Otros conceptos importantes relativos a la *POO*:

* ***Interfaz***: es un contrato que la clase que la implemente debe cumplir. En ella se definen ciertos métodos y propiedades que las clases deben implementar. No son más que una guía para asegurar que las clases que las implementen siguen ciertas reglas.
En general se nombran en *PascalCase* con una I en el inicio.
Se usan sobre todo para utilizar patrones de diseño y asegurar que el código es coherente.

```csharp
interface IBase
{
  string Name { get; set; }
  int Hours { get; set; }
}

struct Estruct: IBase
{
  public string Name { get; set; }
  public int Hours { get; set; }
  public Estruct(string name, int hours)
  {
    this.Name = name;
    this.Hours = hours;
  }
}

class Clase
{
  public string Name { get; set; }
  public int Hours { get; set; }
  public Clase(string name, int hours)
  {
    this.Name = name;
    this.Hours = hours;
  }
}
```

> Si *Clase* o *Estruct* no definieran Name o Hours, se mostraría un error diciendo que no implementan la interfaz *IBase*
