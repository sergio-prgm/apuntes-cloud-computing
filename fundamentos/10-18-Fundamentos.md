# Día 4

## Práctica de POO

Vamos a crear una clase *Perro* para ver cómo funcionan las clases:

```csharp
private static void Main(string[] args)
{
  Perro Perrico = new("Doberman", 20.6, "Perrico");
  Perro Juanico = new("Yorkshire", 6, "Juanico");
  Perrico.Characteristics();
}

public class Perro
{
    // Constructor
  public Perro(string raza, double peso, string nombre)
  {
    this.raza = raza;
    this.peso = peso;
    this.nombre = nombre;
  }

  // Atributos
  public string? raza { get; set; }
  public double peso { get; set; }
  public string? nombre { get; set; }

  const int EdadDePerro = 6;

  // Métodos
  public void Comer()
  {
    Console.WriteLine($"{nombre} está comiendo");
  }
  public void Ladrar()
  {
    Console.WriteLine($"{nombre} está ladrando!!");
  }
}
```

## Definiciones de POO

* *Miembros*: todos los elementos de los que se compone una clase. *Propiedades* y *Métodos* son tipos de miembros.

* *Propiedades*: son propiedades de la clase qué existirán en cada una de las instancias de la misma. Pueden tener valores fijos (estáticos, constantes, etc. como <code>EdadDePerro</code>) o pueden ser distintos para cada instancia.

* *Constructor*: función que se debe llamar para instanciar una clase. Se suele utilizar para asignar valores a los atributos variables de dicha instancia.

* *Métodos*: son funciones que, generalmente, utilizan datos propios de la clase en la que se encuentran y que son propios de dichas clases, pudiendo modificar las variables entre otras funcionalidades.

Para instanciar una clase debe usarse la palabra especial <code>new</code> seguido del nombre de la clase y, si los tiene, los argumentos del constructor entre paréntesis.
Cada instancia de una clase es un objeto.

Para acceder a las propiedades o métodos públicos de la clase se usa la notación de punto (ej. <code>Perrico.raza</code> o <code>Perrico.Comer()</code>).

## Estructuras de datos

Nombre | Tamaño | Tipo | Características
--- | --- | --- | --- |
Array | Estático | Estático |
List | Dinámico | Estático |
ArrayList | Dinámico | Dinámico |
Queue | Dinámico | Dinámico\* | FiFo\**
Stack | Dinámico | Dinámico\* | FiLo\**
Dictionary | Dinámico | Estático | Clave-Valor
SortedList | | | Clave-Valor · Se puede acceder a los valores mediante la clave o mediante el índice

> **\*** Se puede pasar un *tipo genérico* al instanciar estas estructuras, en cuyo caso pasan a ser de tipo estático.

> **\*\*** Al iterar con un foreach sobre estas estructuras se recorren de la misma manera en la que se editan, es decir, *Queue* se recorre de inicio a fin y *Stack* se recorre de fin a inicio.

### Matriz *Array*

Tipo de colección más básico. De hecho, es el único tipo de colección que no viene de <code>System.Collections</code>. El tamaño y el tipo se deben declarar al instanciar un nuevo *Array* y no se pueden variar (también se puede declarar con el tipo *object* que permite utilizar cualquier tipo de variable).

Útil para cuando simplemente se necesita una colección con valores del mismo tipo a la que no se van a realizar muchas modificaciones.

```csharp
int[] array1 = new int[5];
int[] array2 = new int[] {1, 3, 5, 7, 9};

object[] array3 = new object[4];
array3[0] = 1;
array3[1] = "palabra";
array3[4] = 2; // Causa una excepción IndexOutOfRangeException
// Poner array con arrays
```

### Lista *List*

*List* es muy similar a *Array*, siendo la mayor diferencia entre las dos que en *List* las dimensiones son variables. Esto permite realizar un gran número de operaciones sobre este tipo de colecciones, motivo por el que son de las más utilizadas.

```csharp
List<int> lista = new(); // Inicia una lista de int vacía
lista[0] = 3;
lista.Add(4);
lista.Remove(4); // Elimina el elemento especificado. Devuelve un bool

char[] arrayChar = { 'e', 'w', 'q', 'w'};
List<char> lista2 = new(arrayChar);

List<float> floatList = new() { 2.3f, 3.4f, 5.4f};
```

### Pila *Stack*

```csharp
```

### Cola *Queue*

```csharp
```

### Diccionario *Dictionary*

```csharp
```

### SortedList

```csharp
```

---
