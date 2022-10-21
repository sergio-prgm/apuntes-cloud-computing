# Laboratorio 2

## Ejercicio 1

Anotar la información necesaria para definir un curso y sus tipos de datos

Name | Tipo de datos | Justificación
------------|-----------------|--------------
Título | string | título del curso
Duración | int | duración en semanas
Horas de crédito | int | número de horas de instrucción
Profesor | string | nombre del profesor del curso
Promedio de calificaciones | double | media de las calificaciones obtenidas
Descripción | string | descripción del curso

## Ejercicio 2: variables de tipos numéricos

Iniciar un [nuevo proyecto](/fundamentos/10-14-Fundamentos.md#iniciar-un-proyecto-de-c-con-visual-studio) en Visual Studio y eliminar el contenido por defecto. A continuación iremos creando los campos que hemos definido en el ejercicio anterior.

### Mejores prácticas: nombrar variables

> En todos los lenguajes de programación existen convenciones y estándares para normalizar el nombramiento de variables y métodos. Conviene seguir una serie de reglas para facilitar el desarrollo propio y grupo, además de que ayuda a entender el código de librerías y frameworks que utilicemos. En general, lo más importante es que los nombres de las variables sean lo más explícitos posible (no importa si ocupan más espacio).

> En cuanto a C# el método más establecido para el nombramiento de variables es *"camelCase"*. Sin embargo, en Python las variables se suelen nombrar siguiendo el estilo "snake_case".

### Tarea 1: declarar variables de datos numéricos

```csharp
int courseID;
int lengthInWeeks;
double myGPA;
```

### Tarea 2: asignar un valor a las variables declaradas

```csharp
courseID = 101;
lengthInWeeks = 10;
myGPA = 0.0;
```

### Tarea 3: enviar las variables (numéricas) a la consola

```csharp
Console.WriteLine(courseID);
Console.WriteLine(lengthInWeeks);
Console.WriteLine(myGPA);
```

> Si bien en los ejercicios primero se declaran y luego se asigna un valor a las variables este proceso se puede simplificar en un solo paso como veremos a continuación.

## Ejercicio 3: variables de tipos de datos textuales

### Tarea 1 y 2: declarar y asignar variables de datos textuales

A continuación se muestra la manera de declarar y usar variables en un solo paso. Esto suele facilitar la legibilidad y hace el código más conciso y compacto.

```csharp
string courseTitle = "CS101"; 
string courseDescription = "This course teaches indtroductory programming topics.";
string instructorName = "MCT Name";
```

### Tarea 3: enviar las variables (strings) a la consola

```csharp
Console.WriteLine(courseTitle);
Console.WriteLine(courseDescription);
Console.WriteLine(instructorName);
```

### Ejercicio 4: variables booleanas

### Tarea 1 y 2: declarar y asignar variables booleanas

```csharp
bool doesExist = true;
bool passingGrade = true;
bool isEnrolled = false;
```

### Tarea 3: enviar las variables (bool) a la consola

```csharp
Console.WriteLine(doesExist);
Console.WriteLine(passingGrade);
Console.WriteLine(isEnrolled);
```

## Ejercicio 5:  declarar y usar constantes

## Constantes

Los valores constantes son valores fijos y que no cambian a lo largo del ciclo de uso de la aplicación o el programa en el que se usan.
> Generalmente las constantes se escriben con *"PascalCase"* en C#, mientras que en Python se usa *"MACRO_CASE"*.

### Tarea 1: declarar constantes

```csharp
const int ThreeCreditWeeks = 5;
const int SixCreditWeeks = 10;
```

### Tarea 2: enviar los valores a consola

```csharp
Console.WriteLine(ThreeCreditWeeks);
Console.WriteLine(SixCreditWeeks);
```
