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

- *Atributos*: son propiedades de la clase qué existirán en cada una de las instancias de la misma. Pueden tener valores fijos (estáticos, constantes, etc. como <code>EdadDePerro</code>) o pueden ser distintos para cada instancia.

- *Constructor*: función que se debe llamar para instanciar una clase. Se suele utilizar para asignar valores a los atributos variables de dicha instancia.

- *Métodos*: son funciones que, generalmente, utilizan datos propios de la clase en la que se encuentran y que son propios de dichas clases, pudiendo modificar las variables entre otras funcionalidades.

Para instanciar una clase debe usarse la palabra especial <code>new</code> seguido del nombre de la clase y, si los tiene, los argumentos del constructor entre paréntesis.
Cada instancia de una clase es un objeto.

Para acceder a los atributos o métodos públicos de la clase se usa la notación de punto (ej. <code>Perrico.raza</code> o <code>Perrico.Comer()</code>).

## Fibonacci

Hacer la secuencia de Fibonacci con *for*, con *while* y de forma recursiva.

### Fibonacci *for*

```csharp
public static List<int> FibonacciFor(int n)
{
  int n1 = 0;
  int n2 = 1;
  List<int> result = new() { n1, n2 };
  for (var i = 2; i < n; i++)
  {
    result.Add(result[i - 1] + result[i - 2]);
  }
  return result;
}
```

### Fibonacci *while*

```csharp
public static List<int> FibonacciWhile(int n)
{
  int n1 = 0;
  int n2 = 1;
  int i = 2;
  List<int> result = new(n) { n1, n2 };
  while (i < n)
  {
    result.Add(result[i - 1] + result[i - 2]);
    i++;
  }
  return result;
}
```

### Fibonacci *recursivo*

```csharp
public static int FibonacciRecursive(int n)
{
  if (n == 2 || n == 1)
    return n - 1;
  return FibonacciRecursive(n - 1) + FibonacciRecursive(n - 2);
}
```

> **Función recursiva**: función que se llama a sí misma. Debe tener un punto de terminación o caso base que detenga la ejecución de la función, porque si no se implementa se produce un bucle infinito.

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

## Laboratorio 4: estructuras de datos y algoritmos

### Ejercicio 1: pseudocódigo

#### Tarea 1: escribir pseudocódigo

```ts
function populateList(list: array, item: {name: string, description: string}): void {
  list.push(item)
}

function displayList(list: array): void {
  list.foreach(item => console.log(item))
}

function removeListItem(list: array, itemName: string): void {
  list.remove(itemName)
}
```

#### Tarea 2: taducir pseudocódigo

```chsarp
static void populateList(List list, string name) {}
static void displayList(List list) {}
static removeListItem(List list, string itemName) {}
```

### Ejercicio 2: creación de estructuras de datos

#### Tarea 1: crear una matriz(*Array*)

```csharp
private static void Main(string[] args)
{
  float[] gradesArray = new float[5];
  addGrades(gradesArray);
  displayGrades(gradesArray);
}
static void addGrades(float[] gradesArray)
{
  gradesArray[0] = 98;
  gradesArray[1] = 99;
  gradesArray[2] = 89;
  gradesArray[3] = 95;
  gradesArray[4] = 96;
}

static void displayGrades(float[] gradesArray)
{
  foreach (double item in gradesArray)
    Console.WriteLine(item);
}
```

#### Tarea 2: implementar una pila(*Stack*)

> **Nota sobre las estructuras de datos**: al implementar algunas estructuras de datos en C# se pueden utilizar lo que se conoce como *tipos genéricos*, que es una manera de declarar el tipo de variables que se almacenarán dentro de estas estructuras. El problema es que algunos métodos no se corresponden a los que no utilizan estos tipos y pueden llevar a errores. Por eso, a no ser que sea necesario declarar explícitamente el *tipo genérico* de las estructuras de datos, es conveniente revisar cuales están siendo empleados. Para ello, basta con ir al inicio del archivo y ver si existe una declaración parecida a <code>using System.Collections.Generics;</code>

> Nota de la nota: los tipos genéricos pueden ser de gran utilidad y no deben verse como una mala opción.

```csharp
// Dentro de Main(), inmediatamente después de displayGrades...
  Stack myStack = new Stack();
  pushStack(gradesArray, myStack);
  popStack(myStack);
  popStack(myStack);
  // ...
}

static void pushStack(float[] gradesArray, Stack stack)
{
  foreach (float item in gradesArray)
    stack.Push(item);
}

static void popStack(Stack stack)
{
  Console.WriteLine("Item removed from the stack: ");
  float item = (float)stack.Pop()!; // El ! al final es para que no salga el subrayado verde
  Console.WriteLine(item);
}
```

#### Tarea 3: implementar una lista

```csharp
// Dentro de Main(), después de popStack...
  SortedList myCourses = new SortedList();
  populateList(myCourses);
  displayList(myCourses, "CS201");
  removeListItem(myCourses, "CS201");
}
static void populateList(SortedList list)
{
  list.Add("CS101", "Introduction to Computer Science");
  list.Add("CS102", "Data Structures and Algorithm Analysis");
  list.Add("CS201", "Introduction to Databases");
  list.Add("CS301", "Introduction to Object-Oriented Programming");
}

static void displayList(SortedList list, string key)
{
  int index;
  string course;
  index = list.IndexOfKey(key);
  course = (string)list.GetByIndex(index)!;
  Console.WriteLine(course);
}

static void removeListItem(SortedList list, string key)
{
  int index;
  string course;
  index = list.IndexOfKey(key);
  course = (string)list.GetByIndex(index)!;
  list.Remove(key);
  Console.WriteLine($"{course} was removed from the list.");
}
```
