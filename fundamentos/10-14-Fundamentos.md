# Día 2

## Iniciar un proyecto de C\# con Visual Studio

Para comenzar con los ejercicios de laboratorio:

1. Abrir Visual Studio 2022.
2. Elegir la opción <strong>Crear nuevo proyecto</strong>.
3. Seleccionar C# en la lista desplegable de lenguajes y elegir <strong>Aplicación de consola</strong>.
4. Dar un nombre al proyecto, elegir el directorio en el que será creado y clic en siguiente.
5. Elegir la opción <strong>.NET 6.0 (Long-term support)</strong> y clic en siguiente (Este paso puede tardar varios minutos).
6. Cuando todo está listo debe aparecer algo similar al [ejercicio 1](#ejercicio-1)

## **Algoritmo**

> Conjunto de instrucciones sistemáticas que permite realizar un cálculo y hallar una solución a una tarea.
>Un algoritmo debe:
>
> * Resolver un problema para el que fue formulado.
> * Buscar en apuntes

## Tipos de datos: (poner todos los tipos de números y eso)

### Tipos numéricos

Estos tipos varian dependiendo de cada lenguaje y de su implementación. Normalmente se distinguen entre tipos enteros y número decimales (de coma flotante)

En el caso de *Python* solo existe esa distinción entre *int* (entero) y *float* (de coma flotante).

En el caso de *C#* existen más tipos de datos dependiendo de cuanta memoria ocupan y si tienen signo o no.

* Enteros:
  Nombre | Espacio en memoria | Signo | Rango de valores
  --- | --- | --- | ---
  sbyte | 8b | +/- | -128 ~ 127
  byte | 8bit | + | 0 ~ 255
  short |  16bit | +/- | -32.768 ~ 32.767
  ushort | 16bit | + | 0 ~ 65.535
  int | 32bit| +/- | -2.147.483.548 ~ 2.147.483.547
  uint | 32bit | + | 0 ~ 4.294.967.295
  long | 64bit | +/- | -9.223.372.036.854.775.808 ~ 9.223.372.036.854.775.807
  ulong | 64bit | + | 0 ~ 18.446.744.073.709.551.615
  nint | 64 o 32bit | +/- | Depende de la plataforma
  nuint | 64 o 32bit | - | Depende de la plataforma

* De coma flotante:
  Nombre | Espacio en memoria | Signo | Rango de valores
  --- | --- | --- | ---
  float | 4byte| |
  double | 8byte | |
  decimal | 16byte | |
  