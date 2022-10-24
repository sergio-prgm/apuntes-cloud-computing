# Laboratorio 8: POO

## Lab A: herencia

### Ejercicio 1: creación de una clase base

#### Tarea 1: crear una clase base para uso genérico

```csharp
namespace ClassTracker;

internal class Course
{
  private string courseTitle;
  private int creditHours;
  private string program;

  public string CourseTitle
  {
    get { return courseTitle; }
    set { courseTitle = value; }
  }

  public int CreditHours
  {
    get { return creditHours;  }
    set { creditHours = value; }
  }

  public string Program
  {
    get { return program; }
    set { program = value; }
  }

  public void EnrollStudent(string studentName)
  {

  }
  
  public virtual float CalculateAverage(float[] arrGrades)
  {
      float avg = 0;
      return avg;
  }
}
```

### Ejercicio 2: heredar de una clase base

#### Tarea 1: crear subclase que hereda de clase base

```csharp
// En CreditCourse.cs
namespace ClassTracker;
public class CreditCourse : Course
{

}

// En NonCreditCourse.cs
namespace ClassTracker;
public class NonCreditCourse : Course
{

}
```

#### Tarea 2: inspeccionar la funcionalidad

```csharp
static void Main(strin[] args)
{
  CreditCourse creditCourse = new();
  creditCourse.CourseTitle = "CS101";
  creditCourse.CreditHours = 6;
  creditCourse.Program = "Computer Science";
  creditCourse.EnrollStudent("Tom Thumb");
}
```

## Lab B: poliformismo

### Ejercicio 1: implementación del polimorfismo anulando una función

#### Tarea 1: invalidar un método

```csharp
// En CreditCourse y en NonCreditCourse

public override float CalculateAverage(float[] arrGrades)
{
  float avg = 0;
  float sum = 0;
  int numGrades = arrGrades.Count();
  foreach (float grade in arrGrades)
  {
    sum += grade;
  }
  avg = sum / numGrades;
  return avg;
}
```

#### Tarea 2: Agregar funcionalidad a la subclase

```csharp
// En CreditCourse
public float CalculateGPA(float grade)
{
  char letterGrade;
  float gradePoints = 0.0f;

  if (grade >= 90)
    letterGrade = 'A';
  else if (grade >= 80 && grade <= 89)
    letterGrade = 'B';
  else if (grade >= 70 && grade <= 79)
    letterGrade = 'C';
  else if (grade >= 66 && grade <= 69)
    letterGrade = 'D';
  else
    letterGrade = 'F';

  switch (letterGrade)
  {
    case 'A':
      gradePoints = 4.0f;
      break;
    case 'B':
      gradePoints = 3.0f;
      break;
    case 'C':
      gradePoints = 2.0f;
      break;
    case 'D':
      gradePoints = 1.0f;
      break;
  }

  return gradePoints;
}
```

```csharp
// En NonCreditCourse
public char CalculateGrade(float grade)
{
  char letterGrade;

  if (grade >= 90)
    letterGrade = 'A';
  else if (grade >= 80 && grade <= 89)
    letterGrade = 'B';
  else if (grade >= 70 && grade <= 79)
    letterGrade = 'C';
  else if (grade >= 66 && grade <= 69)
    letterGrade = 'D';
  else
    letterGrade = 'F';
  return letterGrade;
}
```

#### Tarea 3: probar la funcionalidad

```csharp
// Dentro de Main en Program.cs y a continuación de lo anterior (no borrar)
float GPA = creditCourse.CalculateGPA(98.5f);
Console.WriteLine($"Tom Thumb has a GPA of {GPA} in course");

NonCreditCourse nonCreditCourse = new NonCreditCourse();
nonCreditCourse.CourseTitle = "Introduction to Excel";
char grade = nonCreditCourse.CalculateGrade(87.0f);
Console.WriteLine($"Tom also received a {grade} in {nonCreditCourse.CourseTitle}");
```

### Ejercico 2: implementación del polimorfismo mediante sobrecarga

#### Tarea 1: agregar un nuevo constructor

```csharp
// En CreditCourse
public CreditCourse()
{
  this.CourseTitle = "";
  this.CreditHours = 0;
  this.Program = "";
}

public CreditCourse(string title, int credits, string program)
{
  this.CourseTitle = title;
  this.CreditHours = credits;
  this.Program = program;
}
```

#### Tarea 2: probar la nueva funcionalidad

```csharp
// Dentro de Main en Program.cs
CreditCourse newCreditCourse = new();
Console.WriteLine(newCreditCourse.CourseTitle);

CreditCourse newCreditCourse2 = new("CS102", 6, "Computer Science");
Console.WriteLine(newCreditCourse2.CourseTitle);
```
