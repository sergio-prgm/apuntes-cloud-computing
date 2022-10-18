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
List | Dinámico | Estático |
ArrayList | Dinámico | Dinámico |
Queue | Dinámico | Dinámico\* | FiFo\**
Stack | Dinámico | Dinámico\* | FiLo\**
Dictionary | Dinámico | Estático | Clave-Valor

> **\*** Se puede pasar un *tipo genérico* al instanciar estas estructuras, en cuyo caso pasan a ser de tipo estático.

> **\*\*** Al iterar con un foreach sobre estas estructuras se recorren de la misma manera en la que se editan, es decir, *Queue* se recorre de inicio a fin y *Stack* se recorre de fin a inicio.
