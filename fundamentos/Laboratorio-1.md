# Laboratorio 1: introducción a la programación

## Ejercicio 1

Al iniciar el proyecto aparecerá la siguiente línea en el editor:

```csharp
Console.WriteLine("Hello, World!");
```

junto con un comentario (al inicio del documento), que se puede eliminar.

## Ejecutar código en Visual Studio

> Para ejecutar el código sin depurar presionar *ctrl+F5* o clic en el triángulo vacío de la parte superior. También se puede iniciar con el depurador (*F5* o clic en el triángulo relleno verde), pero está opción es ligeramente más lenta.

Si todo ha salido bien en la consola aparecerá <code>Hello, World!</code> y un mensaje que termina con <code>exited with code 0</code>, lo que significa que todo ha salido bien y no se ha producido ningún error.

Escribir lo siguiente y volver a ejecutar para ver cómo cambia el resultado:

```csharp
Console.WriteLine("Hello, World of Programming!");
```

## Ejercicio 2

En el segundo ejercicio utilizamos una variable <code>name</code> que almacena el input del usuario. Si se escribe solamente la siguiente línea:

```csharp
Console.WriteLine("Hello, " + name + ". Welcome to the World of Programming!")
```

<code>name</code> aparecerá en rojo y el comando no se podrá ejecutar. Esto pasa porque estamos utilizando una variable sin haberla inicializado

```csharp
Console.WriteLine("What is your name?");
var name = Console.ReadLine();
Console.WriteLine("Hello " + name + " and welcome.");
```

> Con el destornillador de la derecha elegir la opción: <code>Convert to 'Program.Main' style program</code> para convertir a la manera más "tradicional" de estructurar el programa.

```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        Console.WriteLine("What is your name?");
        var name = Console.ReadLine();
        Console.WriteLine("Hello " + name + " and welcome to the world of programming.");
    }
}
```
