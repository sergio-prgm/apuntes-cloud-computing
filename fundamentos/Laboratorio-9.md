# Laboratorio 9: seguridad y rendimiento

## Ejercicio 1: conversión de tipos

### Tarea 1: convertir tipo valor a referencia

```csharp
Object[] myArray = new object[3];
int myInt = 5;
string myString = "Hello";
char myChar = 'A';

myArray[0] = myInt;
myArray[1] = myString;
myArray[2] = myChar;

double myDouble;
myDouble = myInt;
myInt = (int)myDouble;
```

### Tarea 2: convertir tipo referencia a valor

```csharp
myInt = (int)myArray[0];
myString = (string)myArray[1];
myChar = (char)myArray[2];
```
