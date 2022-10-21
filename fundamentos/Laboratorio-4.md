# Laboratorio 4: estructuras de datos y algoritmos

## Ejercicio 1: pseudocódigo

### Tarea 1: escribir pseudocódigo

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

### Tarea 2: taducir pseudocódigo

```chsarp
static void populateList(List list, string name) {}
static void displayList(List list) {}
static removeListItem(List list, string itemName) {}
```

## Ejercicio 2: creación de estructuras de datos

### Tarea 1: crear una matriz(*Array*)

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

### Tarea 2: implementar una pila(*Stack*)

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

### Tarea 3: implementar una lista

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
