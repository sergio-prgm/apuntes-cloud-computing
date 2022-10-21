# Fibonacci

Hacer la secuencia de Fibonacci con *for*, con *while* y de forma recursiva.

## Fibonacci *for*

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

## Fibonacci *while*

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

## Fibonacci *recursivo*

```csharp
public static int FibonacciRecursive(int n)
{
  if (n == 2 || n == 1)
    return n - 1;
  return FibonacciRecursive(n - 1) + FibonacciRecursive(n - 2);
}
```

## Recursividad

> **Función recursiva**: función que se llama a sí misma. Debe tener un punto de terminación o caso base que detenga la ejecución de la función, porque si no se implementa se produce un bucle infinito.
