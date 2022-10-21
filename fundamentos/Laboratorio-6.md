# Laboratorio 6: *I/O*

## Generar archivo de clase en Visual Studio

Para este laboratorio se parte de una serie de archivos con bastante contenido en ellos.
Hay dos archivos de clases normales (*Student* e *Instructor*) y uno de una clase abstracta (*Person*).
Para crear nuevos archivos de clase en Visual Studio hay que:

1. Clic derecho sobre el proyecto en el que se quiera crear la nueva clase
2. Seleccionar *Agregar* - *Clase*
3. Escribir el nombre que se desee para la clase y clic en *Agregar*

```csharp
// Fichero Person.cs
namespace Laboratorio_6
{
  abstract class Person
  {
    private float height;
    private float weight;
    private string gender;
    private int age;
    private string firstName;
    private string lastName;

    public float Height
    {
      get { return height; }
      set { height = value; }
    }

    public float Weight
    {
      get { return weight; }
      set { weight = value; }
    }

    public string Gender
    {
      get { return gender; }
      set { gender = value; }
    }

    public int Age
    {
      get { return age; }
      set { age = value; }
    }

    public string FirstName
    {
      get { return firstName; }
      set { firstName = value; }
    }

    public string LastName
    {
      get { return lastName; }
      set { lastName = value; }
    }

    public virtual void eat()
    {
      Console.WriteLine("lurping");
    }

    public void sleep()
    {
      Console.WriteLine("Snorting");
    }

    public abstract void move();

    public void communicate() { }
  }
}
```

> Esta manera de declarar todas las propiedades de la clase es muy verbososo y repetitivo. En C#, si una propiedad no necesita de ninguna lógica para leer *get* o establecer *set* se pueden declarar como *propiedades auto-implementadas*.

```csharp
public float Height { get; set; }
public float Weight { get; set; }
public string Gender { get; set; }
public int Age { get; set; }
public string FirstName { get; set; }
public string LastName { get; set; }
```

## Modificadores *abstract* y *virtual*

> **Nota sobre *clases abstractas***: las clases abstractas son un tipo de clases que no se pueden instanciar y se suelen usar como clase *base* para crear clases que hereden de ella. En este caso la clase *Person* sirve de base para crear las clases *Student* e *Instructor*.

> **Nota sobre campos *virtual* y *abstract***: este tipo de campos (métodos, propiedades, etc.) suelen usarse dentro de clases abstractas o, en el caso de *abstract*, en interfaces. De forma similar a las clases, los campos con *abstract* son campos que no tienen implementación y debe hacerse dentro de la clase que herede (o la interfaz que implemente) de la clase en la que se declara. En este caso, el método *move* requiere de una implementación en *Student* y en *Instructor*. Los campos con *virtual* son campos que tienen implementación definida dentro de la clase base pero se pueden sobreescribir (*override*) en cada una de las implementaciones de dicha clase. Por ejemplo, se podría definir un método para *eat()* especial en *Student*.

```csharp
// En Student.cs
internal class Student: Person
{
  // ...
  public override void eat() => Console.WriteLine("Eat more");
}
```

---

```csharp
// Fichero Student.cs
namespace Laboratorio_6
{
  internal class Student: Person
  {
    public Student(string first, string last, string gender, int age)
    {
      this.FirstName = first;
      this.LastName = last;
      this.Gender = gender;
      this.Age = age;
    }

    public override void move() { }
  }
}
```

```csharp
// Fichero Instructor.cs
namespace Laboratorio_6
{
  class Instructor: Person
  {
    public Instructor(string first, string last, string gender, int age)
    {
      this.FirstName = first;
      this.LastName = last;
      this.Gender = gender;
      this.Age = age;
    }

    public override void move() { }
  }
}
```

```csharp
// En Program.cs
static void Main(string[] args)
{
    // E1 Tarea 1
    Console.WriteLine("Do you want to create a:\n");
    Console.WriteLine("S - Student\n");
    Console.WriteLine("I - Instructor\n");
    Console.WriteLine("Q - Quit");
    //

    // E1 Tarea 2
    char response = Convert.ToChar(Console.Read());
    //

    switch (response)
    {
        case 's':
        case 'S':
            CreateStudent();
            break;
        case 'i':
        case 'I':
            CreateInstructor();
            break;
        case 'q':
        case 'Q':
            Environment.Exit(0);
            break;
    }
    static void CreateStudent()
    {
        string first, last, gender;
        int age;

        Console.ReadLine();

        Console.WriteLine("Enter the student's first name.");
        first = Console.ReadLine();

        Console.WriteLine("Enter the student's last name.");
        last = Console.ReadLine();

        Console.WriteLine("Enter the student's gender.");
        gender = Console.ReadLine();

        Console.WriteLine("Enter the student's age (please input a number).");
        age = Convert.ToInt32(Console.ReadLine());

        Student newStudent = new Student(first, last, gender, age);
    }

    static void CreateInstructor()
    {
        string first, last, gender;
        int age;

        Console.ReadLine();

        Console.WriteLine("Enter the instructor's first name.");
        first = Console.ReadLine();

        Console.WriteLine("Enter the instructor's last name.");
        last = Console.ReadLine();

        Console.WriteLine("Enter the instructor's gender.");
        gender = Console.ReadLine();

        Console.WriteLine("Enter the instructor's age.");
        age = Convert.ToInt32(Console.ReadLine());

        Instructor newInstructor = new Instructor(first, last, gender, age);
    }

    static void SaveToFile(Person person)
    {
        string fileName;
        string header;
        if (person is Student)
        {
            fileName = "Students.txt";
            header = "Students";
            WriteContents(header, fileName, person);
            ReadFile(fileName);
        }
        else
        {
            fileName = "Instructors.txt";
            header = "Instructors";
            WriteContents(header, fileName, person);
            ReadFile(fileName);
        }
    }
  }
}

```

## Ejercicio 1: leer y escribir con la consola

### Tarea 1: mostrar output en la consola

### Tarea 2: leer input de la consola

Las dos tareas anteriores se encuentran ya resueltas en el código anterior entre <code>// E1 Tarea</code>.

## Ejercicio 2: leer y escribir archivos

### Tarea 1: escribir archivos de texto

```csharp
static void CreateStudent()
{
  // ...
  SaveToFile(newStudent)
}

static void CreateInstructor()
{
  // ...
  SaveToFile(newInstructor)
}

static void WriteContents(string header, string fileName, Person person)
{
    if (!File.Exists(fileName))
    {
        StreamWriter writer = new StreamWriter(fileName);

        writer.WriteLine(header);
        writer.Write(person.FirstName + ", ");
        writer.Write(person.LastName + ", ");
        writer.Write(person.Gender + ", ");
        writer.Write(person.Age);
        writer.Close();
    }
    else
    {
        StreamWriter writer = File.AppendText(fileName);

        writer.WriteLine();
        writer.WriteLine($"{person.FirstName}, {person.LastName}, {person.Gender}, {person.Age}");
        writer.Close();
    }
}
```

## Ejecutar en *Debug* vs normal

> Al ejecutar este programa desde Visual Studio, los archivos que se crean se almacenan dentro de una carpeta *Debug*(/bin/Debug/net6.0/). Si se ejecuta fuera de Visual Studio se guarda en la carpeta correspondiente al proyecto (en mi caso dentro de Laboratorio_6).

Para ejecutar un programa fuera de Visual Studio:

1. Abrir una terminal (en el menú de Windows escribir "cmd" o "símbolo del sistema").
2. Ir a la carpeta en la que se encuentra (también se puede ir a la carpeta en la que se encuentra el proyecto, clic derecho abrir con símbolo del sistema)
3. Escribir en la terminal:

```powershell
dotnet run Program.cs
```

## Tarea 2: leer archivos de texto

```csharp
static void SaveToFile(Person person)
{
  // ...
  if (person is Student)
  {
    // ...
    ReadFile(fileName);
  }
  else
  {
    // ...
    ReadFile(fileName);
  }
}

// ...
static void ReadFile(string fileName)
{
  Console.WriteLine("The file was saved with the following content:");

  StreamReader reader = new StreamReader(fileName);
  Console.WriteLine();
  Console.WriteLine(reader.ReadToEnd());
}
```
