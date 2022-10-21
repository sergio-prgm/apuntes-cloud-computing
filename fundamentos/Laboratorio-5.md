# Laboratorio 5: Bugs y Errores

## Ejercicio 1: Creación de controladores de excepciones estructurados

### Tarea 1: try-catch

```csharp
Console.WriteLine("Enter the credit hours for this course");
// newCourse.creditHours = Console.ReadLine(); 
// Produce un error porque ReadLine() devuelve un string
// y tanto creditHours como gradePoints son int
newCourse.creditHours = Convert.ToInt32(Console.ReadLine());

Console.WriteLine("Enter the grade points for this course");
// newCourse.gradePoints = Console.ReadLine();
newCourse.gradePoints = Convert.ToInt32(Console.ReadLine());

courseList[counter] = newCourse;
```

Si bien el código se ejecuta correctamente, no tiene en cuenta posibles errores producidos por el usuario. Para solucionar estos errores se envuelve este código en un bloque try-catch en el que se captura un error de conversión *InvalidCastException* que se produce, por ejemplo, cuando el usuario introduce un *string* en lugar de un *int*.

```csharp
Console.WriteLine("Enter the credit hours for this course");
try
{
  newCourse.creditHours = Convert.ToInt32(Console.ReadLine());
  Console.WriteLine("Enter the grade points for this course");
  newCourse.gradePoints = Convert.ToInt32(Console.ReadLine());
  courseList[counter] = newCourse;
}
catch (InvalidCastException ex)
{
  Console.WriteLine(ex.Message);
}
```

### Tarea 2: try-catch-finally

```csharp
// Después del catch anterior
finally
{
  GC.Collect(); // Limpia el recolector de memoria
}
```

### Tarea 3: probar manejo de errores

## Ejercicio 2: depurador de Visual Studio
