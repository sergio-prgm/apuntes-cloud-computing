# Día 5

> Conversión de tipos

## Namespaces de las colecciones

> System.Collections.Generic

> System.Collections.Concurrent

> System.Collections

### Namespaces

Un namespace es un contenedor que se usa para organizar el código y establecer ámbitos de uso de las distintas clases. Si el namespace afecta a todo el archivo se puede declarar simplemente al inicio del mismo.

```csharp
namespace esteFichero;
public class clase
{
  int años;
}

public class banco
{
  int longitud;
}
```

```csharp
namespace esteFichero
{
  public class Clase
  {
    public int años;
  }

  public class Banco
  {
    public int longitud;
  }
  
  namespace OtraCosa
  {
    public class Mesa
    {
      public int patas;
    }
  }
}
```

Todo lo declarado dentro de un namespace se puede utilizar dentro del mismo, pero, para utilizarlo en otros namespaces, hay dos modos de hacerlo:

* "Importar" el namespace con la palabra clave *using* en el inicio del fichero:

  ```csharp
  // En program.cs

  using esteFichero;
  using esteFichero.OtraCosa;

  internal class Program
  {
    private static void Main(string[] args)
    {
      Banco banco = new();
      banco.longitud = 3

      Mesa mesa = new();
      mesa.patas = 4;
    }
  }
  ```

* Usar la "notación de puntos" para usar cada una de las clases del namespace:

  ```csharp
  // En program.cs

  internal class Program
  {
    private static void Main(string[] args)
    {
      esteFichero.Banco banco = new();
      banco.longitud = 3;

      esteFichero.OtraCosa.Mesa mesa = new();
      mesa.patas = 4;
    }
  }
  ```

### Métodos de colecciones

[Definiciones de las colecciones](/fundamentos/10-18-Fundamentos.md#estructuras-de-datos)

```csharp

```

## Depuración *Debugging* y Errores (módulo 5)

### Tipos de errores

* **Sintácticos**: normalmente el IDE o editor de texto es capaz de notificar de este tipo de errores.
* **Lógicos**: comportamientos inesperados en la lógica del programa. Se descubren al ejecutar el código y son más difíciles de detectar. La depuración suele ser el mejor método para localizar y atajar este tipo de errores.
* **Interacción del usuario**: para localizar estos errores y dotar de salvaguardas(??) al programa se utilizan distintas estrategias de *testing* (E2E, integración, unitarios, etc.).

### Tratamiento de errores

* Estructurado:

  * Try-Catch-Finally: el programa tratará de ejecutar el contenido de *try* y, si se produce algún error, irá pasando por cada *catch* y evaluando los filtros (el contenido entre paréntesis) de cada uno. Si se utiliza un *catch* sin filtro (*catch all*), atrapará cualquier tipo de error. La sentencia *finally* se usa para ejecutar un conjunto de instrucciones independientemente de si hay error o no.

    Este tipo de sentencias deben tener siempre al menos un *catch* o un *finally*.

  ```csharp
  try
  {
    result = numerator / denominator;
    
    Console.WriteLine();
    Console.WriteLine("The result is: " + result);
  }
  catch (DividedByZeroException dEx)
  {
    Console.WriteLine(dEx);
  }
  catch (Exception e)
  {
    Console.WriteLine(e);
  }
  finally
  {
    Console.WriteLine("End of the try-catch-finally block.");
  }
  ```

### Depuración *Debugging*

Es el proceso de eliminar todos los errores inesperados (sobre todo [errores lógicos](#tratamiento-de-errores))

## Entrada/Salida *I/O* (módulo 6)

> **buscamos documentación sobre I/O en C#**
