# Laboratorio 3: comprender el flujo del programa

## Ejercicio 1: Funciones de ejecución

### Tarea 1: crear una función que no devuelve valor

```csharp
static void SetInstructorName(string newName)
{
  string instructorName = newName;
  Console.WriteLine("Instructor name is " + instructorName);
}
static void SetCourseTitle(string newTitle)
{
}
```

### Tarea 2: llamar a una función que no devuelve valor

```csharp
static void Main(string[] args)
{
  SetInstructorName("John Smith");
}
```

### Tarea 3: crear una función que devuelva un valor

```csharp
static bool ValidateCourseTitleLength(string title)
{
  return true
}
```

### Tarea 4: llamar a una función que devuelve un valor

```csharp
// Dentro de Main
SetCourseTitle("CS 101");
```

---

## Ejercicio 2: implementación de decisiones en el código

### Tarea 1: instrucciones *if*

```csharp
// Modificar ValidateCourseTitleLength()
static bool ValidateCourseTitleLength(string title)
{
  if(title.Length <= 50)
  {
    return true;
  }
  else
  {
    return false;
  }
}
// Modificar SetCourseTitle()
static void SetCourseTitle(string newTitle)
{
  bool result = ValidateCourseTitleLength(newTitle);
  if (result)
  {
    string courseTitle = newTitle;
    Console.WriteLine($"Course title is {courseTitle}");
  }
  else
  {
    Console.WriteLine($"Class name exceeds 50 characters, please shorten.");
  }
}
```

## Mejores prácticas: Números mágicos

> **Sobre el uso de *números mágicos***: en el ejemplo del curso se utiliza un 'número mágico': un número que no se sabe exactamente qué es. No suele ser buena idea usar números de esta forma porque si se quiere modificar su valor hay que hacerlo en todos los lugares en los que se utiliza; además de ser más difícil entender qué es o de dónde viene. Lo normal es que en estos casos se creen una serie de constantes que hagn referencia a estos valores.

```csharp
const int charLimit = 50;
// ...
if (title <= charLimit)
// ...
Console.WriteLine($"Class name exceeds {charLimit} characters, please shorten.");
```

### Tarea 2: instrucciones *if* anidadas

```csharp
static void AddClass(string title, bool isInProgram, bool isRequired, bool isElective)
{
  if (isInProgram)
  {
    if (isRequired)
      Console.WriteLine($"{title} is in the Program and is a required course.");
    else if (isElective)
      Console.WriteLine($"{title} is in the Program and is an elective course.");
    else
      Console.WriteLine($"{title} is in the Program and is an extra credit course.");
  }
  else 
  {
    Console.WriteLine($"{title} is not in the Program.");
  }
}
```

## Mejores prácticas: *if* anidados

> **Sobre los *if* anidados**: si bien existen casos en los que nos podamos sentir tentados a escribir *if* dentro de *if* dentro de *if*... no suele ser buena idea hacerlo así. El motivo principal es que se hace difícil de leer y de entender el flujo de la información, lo que puede (suele) acabar en comportamientos imprevistos y peor experiencia en el desarrollo. Por eso, es buena idea evitar en la medida de lo posible este tipo de situaciones.
Existen varias técnicas para mejorar este código, en este caso se ha implementado la más popular que es crear un *Early Return*, es decir, traer al frente la primera condición excluyente y hacer un *return* que acaba con la ejecución de la función. De esta manera se elimina un nivel de anidación y se ve más clara la intención de la función.

```csharp
static void AddClass(string title, bool isInProgram, bool isRequired, bool isElective)
{
 if (!isInProgram)
 {
  Console.WriteLine($"{title} is not in the Program.");
  return;
 }
 if (isRequired)
  Console.WriteLine($"{title} is in the Program and is a required course.");
 else if (isElective)
  Console.WriteLine($"{title} is in the Program and is an elective course.");
 else
  Console.WriteLine($"{title} is in the Program and is an extra credit course.");
}
```

### Tarea 3: instrucciones *Switch*

```csharp
static void DisplayReminders(string day)
{
 switch (day)
 {
  case "Wednesday":
   Console.WriteLine("Discussion post is due today!");
   break;
  case "Friday":
   Console.WriteLine("Quiz is due today!");
   break;
  case "Sunday":
   Console.WriteLine("Assignment is due today!");
   break;
  default:
   Console.WriteLine("Study new material, nothing due today.");
   break;
 }
}
```

## Mejores prácticas: Switch

> **Nota sobre los switch**: en general, se considera que *switch* no son buena práctica, porque afean el código y hacen que sea más difícil seguirlo. Además, por la sintaxis que emplean, es muy fácil que falte un *break* y salgan errores inesperados.
> Para evitar el uso de *switch* y hacer el código más legible se suelen utilizar Diccionarios (o cualquier estructura de datos de clave-valor) en los que la clave sería equivalente al *case* y el valor sería equivalente a la devolución correspondiente.

```csharp
static Dictionary<string, string> SwitchAlternative = new Dictionary<string, string>
{
 { "Wednesday", "Discussion post is due today!"},
 { "Friday", "Quiz is due today!"},
 { "Sunday", "Assignment is due today!" },
 { "default", "Study new material, nothing due today." }
};

// E2 Tarea 3
static void DisplayReminders(string day)
{
 if (!SwitchAlternative.ContainsKey(day))
 {
  Console.WriteLine(SwitchAlternative["default"]);
  return;
 }
 Console.WriteLine("si", SwitchAlternative[day]);
}
```

---

## Ejercicio 3: estructuras de repetición (bucles)

### Tarea 1: bucle *for*

Para ejecutar el siguiente bucle *for* se crea un <code>Array</code> de <code>double</code> (se instancia con <code>double[]</code> y su contenido entre <code>{}</code>) y se recorre a lo largo de su contenido.

```csharp
static void CalculateAverage()
{
  double[] grades = new double[] { 89, 98, 99, 90, 95 };
  double average = 0.0;
  double total = 0.0;
  int gradeCounter;

  for (gradeCounter = 0; gradeCounter < grades.Length; gradeCounter++)
    total = total + grades[gradeCounter];

  average = total / gradeCounter;
  Console.WriteLine($"Grade average is {average}");
}
```

### Tarea 2: bucle *while*

En el caso del bucle *while* no necesita recorrer ninguna colección o lista, sino que se utilizan las condiciones para detectar el momento de acabar el programa.

- El primer bucle detendrá su ejecución si se introduce un valor que sea mayor o igual a 200, que es el "código de escape" del bucle.
- El segundo bucle se detiene cuando es incapaz de convertir el input en un <code>double</code>.

> El método TryParse() recibe dos argumentos, en este caso: un <code>string</code> (el input del usuario) y la variable en la que se debe almacenar este input en forma de double; y devuelve <code>true</code> o <code>false</code> si ha podido o no convertir el input a double).

```csharp
static void CalculateAverageWithWhile()
{
    double grade = 0.0;
    double total = 0.0;
    int numberOfGrades = -1;

    Console.WriteLine("Enter a grade number, or 200 to end:");
    while (grade < 200)
    {
        numberOfGrades++;
        total = total + grade;
        while (!Double.TryParse(Console.ReadLine(), out grade))
            Console.WriteLine("That's not a valid grade!");
    }
    var average = total / numberOfGrades;
    Console.WriteLine($"Grade average is: {average}");
}
```
