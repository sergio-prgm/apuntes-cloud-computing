# Laboratorio 7: estructuras, objetos y clases

## Ejercicio 1: creación de estructuras

### Tarea 1: crear estructuras

```csharp
namespace Laboratorio_7
{
  static void Main(string[] args)
  {
  }

  struct Course
  {
    public string title;
    public int creditHours;
    public string program;
    public string instructor;

    public Course(string title, int credits, string prog, string inst)
    {
      this.title = title;
      this.creditHours = credits;
      this.program = prog;
      this.instructor = inst;
    }

    public string GetTitle()
    {
      return title.ToUpper();
    }
  }
}
```

### Tarea 2: uso de estructuras

```csharp
namespace Laboratorio_7
{
  static void Main(string[] args)
  {
    Course cs101 = new Course("cs101", 6, "Computer Science", "Mr. Smith");
    
    Course cs102 = new Course();
    cs102.title = "cs102";
    cs102.creditHours = 6;
    cs102.program = "Computer Science";
    cs102.instructor = "Mrs. Jones";

    Console.WriteLine("{0}, {1}, {2}, {3}\n", cs101.title, cs101.creditHours, cs101.program, cs101.instructor);
    Console.WriteLine($"{cs102.title}, {cs102.creditHours}, {cs102.program}, {cs102.instructor}\n");
    Console.WriteLine(cs101.GetTitle());
    Console.WriteLine();
    Console.WriteLine(cs102.GetTitle());
  }

  struct Course
  {
    // ...
  }
}
```

## Ejercicio 2: creación de clases

Crear otro proyecto para probar el uso de las clases o cambiar el nombre de la clase o de la estructura.

[Generar un archivo de clase](Laboratorio-6.md#generar-archivo-de-clase-en-visual-studio) llamado Course.

### Tarea 1: crear archivos de clase

```csharp
namespace Laboratorio_7
{
  internal class CourseC
  {
    public string title;
    public int creditHours;
    public string program;
    public string instructor;

    public CourseC()
    {
    }

    public CourseC(string title, int credits, string prog, string inst)
    {
      this.title = title;
      this.creditHours = credits;
      this.program = prog;
      this.instructor = inst;
    }

    public string GetTitle()
    {
      return title.ToUpper();
    }
  }
}
```

## Sobrecarga *Overloading*

Se refiere a la creación de métodos (también constructores) con el mismo nombre, pero con diferentes firmas y definiciones. Para seleccionar uno u otro se utilizan distinto número y tipo de argumentos al ejecutarlos.
Tanto métodos y funciones como clases permiten el uso de *Overloading*. En el este ejercicio el constructor de CourseC usa esta técnica: tiene uno vacío y otro al que hay que pasarle *title*, *credits*, *prog* e *inst*.

### Tarea 2: encapsular datos y funcionalidad en una clase

```csharp
namespace Laboratorio_7
{
  internal class CourseC
  {
    private string _title;
    private int _creditHours;
    private string _program;
    private string _instructor;

    private string Title
    {
      get { return this._title; }
      set { this._title = value; }
    }

    public int CreditHours
    {
      get { return this._creditHours; }
      set
      {
        if (value >= 3 || value <= 6)
        {
          this._creditHours = value;
        }
      }
    }

    public string Program
    {
      get { return this._program; }
      set { this._program = value; }
    }

    public strin Instructor
    {
      get { return this._instructor; }
      set { this._instructor = value; }
    }

    public CourseC()
    {
    }

    public CourseC(string title, int credits, string prog, string inst)
    {
      this._title = title;
      this._creditHours = credits;
      this._program = prog;
      this._instructor = inst;
    }

    public string GetTitle()
    {
      return this._title.ToUpper();
    }
  }
}
```

```csharp
namespace Laboratorio_7
{
  static void Main(string[] args)
  {
    CourseC cs101 = new CourseC("cs101", 6, "Computer Science", "Mr. Smith");
    
    CourseC cs102 = new CourseC();
    cs102.title = "cs102";
    cs102.creditHours = 6;
    cs102.program = "Computer Science";
    cs102.instructor = "Mrs. Jones";

    Console.WriteLine("{0}, {1}, {2}, {3}\n", cs101.title, cs101.creditHours, cs101.program, cs101.instructor);
    Console.WriteLine($"{cs102.title}, {cs102.creditHours}, {cs102.program}, {cs102.instructor}\n");
    Console.WriteLine(cs101.GetTitle());
    Console.WriteLine();
    Console.WriteLine(cs102.GetTitle());
  }
}
```
