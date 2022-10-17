## Iniciar un proyecto de C\# con Visual Studio
Para comenzar con los ejercicios de laboratorio:
1. Abrir Visual Studio 2022.
2. Elegir la opción <strong>Crear nuevo proyecto</strong>.
3. Seleccionar C# en la lista desplegable de lenguajes y elegir <strong>Aplicación de consola</strong>.
4. Dar un nombre al proyecto, elegir el directorio en el que será creado y clic en siguiente.
5. Elegir la opción <strong>.NET 6.0 (Long-term support)</strong> y clic en siguiente (Este paso puede tardar varios minutos).
6. Cuando todo está listo debe aparecer algo similar al [ejercicio 1](#ejercicio-1) 

## Laboratorio 1
### Ejercicio 1
Al iniciar el proyecto aparecerá la siguiente línea en el editor:
```csharp
Console.WriteLine("Hello, World!");
```
junto con un comentario (al inicio del documento), que se puede eliminar.

> Para ejecutar el código sin depurar presionar *ctrl+F5* o clic en el triángulo vacío de la parte superior. También se puede iniciar con el depurador (*F5* o clic en el triángulo relleno verde), pero está opción es ligeramente más lenta. 

Si todo ha salido bien en la consola aparecerá <code>Hello, World!</code> y un mensaje que termina con <code>exited with code 0</code>, lo que significa que todo ha salido bien y no se ha producido ningún error.

Escribir lo siguiente y volver a ejecutar para ver cómo cambia el resultado:
```csharp
Console.WriteLine("Hello, World of Programming!");
```
### Ejercicio 2 
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

> **Algoritmo:** conjunto de instrucciones sistemáticas que permite realizar un cálculo y hallar una solución a una tarea.
>Un algoritmo debe:
> * Resolver un problema para el que fue formulado.
> * Buscar en apuntes

Tipos de datos: (poner todos los tipos de números y eso)

## Laboratorio 2
### Ejercicio 1
Anotar la información necesaria para definir un curso y sus tipos de datos

Name | Tipo de datos | Justificación
------------|-----------------|--------------
Título | string | título del curso
Duración | int | duración en semanas
Horas de crédito | int | número de horas de instrucción
Profesor | string | nombre del profesor del curso
Promedio de calificaciones | double | media de las calificaciones obtenidas
Descripción | string | descripción del curso

### Ejercicio 2: variables de tipos numéricos
Iniciar un [nuevo proyecto](#iniciar-un-proyecto-de-c-con-visual-studio) en Visual Studio y eliminar el contenido por defecto. A continuación iremos creando los campos que hemos definido en el ejercicio anterior.

> En todos los lenguajes de programación existen convenciones y estándares para normalizar el nombramiento de variables y métodos. Conviene seguir una serie de reglas para facilitar el desarrollo propio y grupo, además de que ayuda a entender el código de librerías y frameworks que utilicemos. En general, lo más importante es que los nombres de las variables sean lo más explícitos posible (no importa si ocupan más espacio).

> En cuanto a C# el método más establecido para el nombramiento de variables es *"camelCase"*. Sin embargo, en Python las variables se suelen nombrar siguiendo el estilo "snake_case".

#### Tarea 1: declarar variables de datos numéricos
```csharp
int courseID;
int lengthInWeeks;
double myGPA;
```
#### Tarea 2: asignar un valor a las variables declaradas
```csharp
courseID = 101;
lengthInWeeks = 10;
myGPA = 0.0;
```
#### Tarea 3: enviar las variables a la consola
```csharp
Console.WriteLine(courseID);
Console.WriteLine(lengthInWeeks);
Console.WriteLine(myGPA);
```

> Si bien en los ejercicios primero se declaran y luego se asigna un valor a las variables este proceso se puede simplificar en un solo paso como veremos a continuación.

### Ejercicio 3: variables de tipos de datos textuales
#### Tarea 1 y 2: declarar y asignar variables de datos textuales
A continuación se muestra la manera de declarar y usar variables en un solo paso. Esto suele facilitar la legibilidad y hace el código más conciso y compacto.
```csharp
string courseTitle = "CS101"; 
string courseDescription = "This course teaches indtroductory programming topics.";
string instructorName = "MCT Name";
```
#### Tarea 3: enviar las variables a la consola
```csharp
Console.WriteLine(courseTitle);
Console.WriteLine(courseDescription);
Console.WriteLine(instructorName);
```

### Ejercicio 4: variables booleanas
#### Tarea 1 y 2: declarar y asignar variables de datos textuales
```csharp
bool doesExist = true;
bool passingGrade = true;
bool isEnrolled = false;
```
#### Tarea 3: enviar las variables a la consola
```csharp
Console.WriteLine(doesExist);
Console.WriteLine(passingGrade);
Console.WriteLine(isEnrolled);
```
### Ejercicio 5:  declarar y usar constantes
Los valores constantes son valores fijos y que no cambian a lo largo del ciclo de uso de la aplicación o el programa en el que se usan.
> Generalmente las constantes se escriben con *"PascalCase"* en C#, mientras que en Python se usa *"MACRO_CASE"*.
#### Tarea 1: declarar constantes
```csharp
const int ThreeCreditWeeks = 5;
const int SixCreditWeeks = 10;
```
#### Tarea 2: enviar los valores a consola
```csharp
Console.WriteLine(ThreeCreditWeeks);
Console.WriteLine(SixCreditWeeks);
```