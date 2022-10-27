# Python Día 2

## Entrada y Salida

Las funciones `input()` y `print()` son las más básicas para interactuar con los programas escritos en Python. `input()` devuelve un string, por lo que, si se quiere utilizar otro tipo de dato (int, float, etc.) se debe hacer una conversión de tipos explícita.

```py
name = input("Please introduce your name: ")
last_name = input("Great, now introduce your last name: ")

print(f"Welcome {name} {lastname}")
id = input(f"Finally, introduce your ID: ")

print(f"Ok {name} {lastname} with ID {id}")
```

## Control de flujo

```py
programador = input("Dime en qué lenguajes programas:")
if programador == "Python":
  print("Asignar a este programador proyectos de Python")
else:
  print("No asignar a este programador proyectos de Python")
```

### Práctica días de la semana

```py
day_dict = {
  1: "Monday",
  2: "Tuesday",
  3: "Wednesday",
  4: "Thursday",
  5: "Friday",
  6: "Saturday",
  7: "Sunday"
}

def dia_semana():
  day_number = int(input("Tell me the number of the day of the week: "))
  if day_number < 1 or day_number > 7:
    print("Not a valid number. Please try again.")
    dia_semana()
  else:
    print(f"Today is {day_dict[day_number]}")

def dia_semana_except():
  day_number = int(input("Tell me the number of the day of the week: "))
  try:
    print(f"Today is {day_dict[day_number]}")
  except KeyError:
    print("Not a valid number. Please try again.")
    dia_semana()
```

## Bucles

Los bucles en Python se realizan de la misma manera que en otros lenguajes (aunque el *for* tiene algunas peculiaridades). Puede resultar extraño pero puede utilizar un *else* al final de un bucle (se ejecuta cuando el bucle recorre todos los elementos y no encuentra ningún break, etc.).

Tanto en el bucle *for* como en el *while* se coloca primero la palabra clave, luego la condición/elemento a recorrer y, por último, dos puntos *:*. Todo lo que se encuentre en un nivel mayor de indentación será el cuerpo del bucle.

### *While*

```py
contador = 1
resultado = 0

while contador <= 100:
  print(f"Voy por el {contador}")
  resultado += contador
  contador += 1
else:
  print(f"El resultado es {resultado}")
```

### *For*

Para ejecutar un bucle *for* hay tres maneras básicas. El primero, es utilizar la función `range()` que genera un rango de números entre el inicio *\_start*, el fin *stop*, y con un *\_step* (inicio y step son opcionales); el segundo es recorrer los elementos de una lista; y el tercero es recorrer una lista con la función `enumerate()` que devuelve una tupla `(index, value)` con la que podremos acceder tanto al índice del elemento como al valor de una manera más concisa.

```py
resultado = 0

for contador in range(1, 101):
  print(f"Voy por el {contador}")
  resultado += contador
else:
  print(f"El resultado es {resultado}")
```

## Funciones

Se usa la palabra clave `def` seguida del nombre de la función, de los parámetros entre paréntesis (o vacíos en caso de que no tenga) y se cierra con unos *:*. `def nombre(argumentos):`
Todo lo que se encuentre en un nivel de indentación mayor al de la función se considera su cuerpo.
El estándar de nombrar las funciones es igual que el de las variables, es decir, con *snake_case*.

```py
def funcion(nombre):
  print(nombre)

funcion("Juan")
funcion(nombre="Paco")
```

> **Sobre las llamadas a funciones**: al llamar la función se pueden utilizar argumentos posicionales (en el mimso orden en el que se encuentran en la definición) o argumentos nombrados (`nombre="Paco"`).

> **Sobre parámetros por defecto**: Python también admite pasar unos valores por defecto a los parámetros (en caso de que no se incluyan en la llamada de la función).

  ```py
  def funcion(nombre = "Por defecto")
    print(nombre)
  
  funcion("Lucas")  # Devuelve "Lucas"
  funcion()         # Devuelve "Por defecto"
  ```

### Modularización de funciones (importar etc.)

Para importar funciones se utiliza la palabra clave `import [module]` seguida del nombre del fichero sin la extensión. Para utilizar sus contenidos se utiliza la notación de punto `module.foo()`.
También se puede añadir `import [module] as [alias]` tras el importe para cambiar el nombre al módulo. Si solo se quiere importar una función se puede utilizar `from [module] import [funcion]`.
Se puede utilizar `import module as *` para utilizar todas las funciones del módulo sin tener que escribir el nombre al inicio. Esto no suele ser recomendado porque distintos paquetes o módulos pueden estar utilizando funciones o clases con el mismo nombre y ocasionar comportamientos inesperados.

Si el archivo se encuentra dentro de una carpeta (/modulo/modulito.py) se debe llamar con notación de puntos `import modulo.modulito`
> Según las reglas de estilo de Python los imports deben colocarse al inicio del fichero.

```py
import utils
utils.foo()

import utils as u
u.foo()

from utils import foo
foo()

# Recomendada solo si se conoce perfectamente los contenidos del módulo
import utils as *
foo()
```

### Práctica funciones: recorrer una lista de diccionarios

Realizar una función que lea una lista de diccionarios y los introduzca en una lista de `str`.

```py
def lista_flores(lista)
  result = []
  for flor in lista:
    result.append(flor["nombre"])
    # result += [flor["nombre"]]    # También funcionaría pero la sintaxis es menos declarativa
  return result
```

A continuación se muestra una solución alternativa utilizando *list comprehension* que es una sintaxis especial de Python para crear listas de manera muy sucinta.

```py
def lista_flores(lista: list[dict]) -> list[str]:
  lista_nombres = [x["nombre"] for x in diccionario_flores]
  return lista_nombres
```
