# Python Día 1

## Introducción

Comentarios con `#` y `"""Comentario multilinea"""`

usar `# -*- utf8 -*-`

Variables con 'snake_case' `mi_variable = 10`

## Tipos sencillos

```py
cadena = "valores"
cade_nota = "cadenota"
entero = 1
flotante = 1.3
booleana = True   # En realidad es un número
infinito = inf    # Importado de math
```

## Operadores aritméticos

```py
1 + 1           # 2
1 - 1           # 0
1 * 2           # 2
1 / 2           # 0.5
1 // 2          # 0 -> rounds down, towards -inf
- 1 // 2        # -1
math.floor(-1 / 2)   # -1 <==> -1 // 2
math.ceil(-1 / 2) # 0 Redonde hacia inf
round(-1 / 2)   # 0 Redondea (si es .5, redondea hacia inf)
```

## Operadores comparativos

```py
a == b                        # Compares value equality
a is b                        # Compares if a and b are in the same memory allocation 
a != b
a >= b and a < 10
a is b or a <= 10
a is not b
a in b
a not in b

true_vals = True, "literally anything else", 3, [1, 2], (1, "hre", False)
false_vals = False, 0, None, [], "", (), {}
```

## Operadores lógicos

```py
5 >= 4 and 5 < 10 # True
5 >= 4 or 5 < 10 # False
```

## Tipos complejos

### Strings (`str`)

Los strings son un tipo de colecciones inmutables, que tienen algunos métodos especiales para operar con ellas (capitalize, center, format, lower, etc.) aparte de los métodos (count e index) y funciones (sorted, len, max, min, etc.) comunes de colecciones .

```py
str1 = "Madrid"
str2 = 'Valencia'
multi_line_str = '''First line
Second line'''
numero = 1 

print("Ciudades: " + str1 + ", " + str2 + str(numero))
print(f"Ciudades: {str1}, {str2}, {numero}")
print("Ciudades: {}, {}, {}".format(t1, t2, numero))
print("Ciudades:", t1, ",", t2, ",", numero)

# Collection operations with strings
check = "Ma" in str1            # Checks if substr exists in str
concat = str1 + " " + str2      # Concat strings
multiply = str1 * 3             # Multiply strings
len_str = len(str1)             # returns length of str
max_str = max(str1)             # returns max value in str
min_str = min(str1)             # returns min value in str

# Str methods
cap_str = str1.capitalize()
case_str = str1.casefold()      # Returns a string suitable for comparison
center_str = str1.center(35, "_") # Returns a str with length n and padding m (or \s by default)
count_str = str1.count("a")
enc_str = str1.encode("utf8")
ends_str = str1.endswith(("al", "id")) # Returns True if str ends with any of n strings
find_str = str1.find("d")       # Returns the lower i of n. Can receive _start and _end params
format_str = "{x} y {y}".format("lluvia", "granizo")
mapped = { "x": 23, "y": 14}
fmap_str = "{x} y {y}".format_map(mapped) # Formats string with values from dict (hash-map)
index_str = str1.index("a")     # Same as .find() but returns Error if not found (find returns -1)
# To be continued
```

### Tuplas (`tuple`)

Colección ordenada de tipos inmutables. Se suelen usar como devolución de funciones y commo índices en diccionarios para implementar colecciones más complejas (grafos, etc.).

```py
tupla = (1, 2, 3, "ele", True, 3.4)
tupla_simple = 1, 2, 3
tupla_desde_lista = tuple([1, 2, 4, 5])

t = 1, 2, 3, 4
1 in tupla                    # Returns True if element exists in tuple
ct = t + (5, 6)               # Concat tuples
mt = 2 * t                    # Multiply the tuple
lt = len(t)                   # Returns the amount of elements in the tuple
maxt = max(t)                 # Returns the max value in tuple
mint = min(t)                 # Returns the min value in tuple
# Index and slice can be used all the same but not to add, remove, replace
tuple_count = t.count(3)      # Returns the number of occurences of n in tuple 
tuple_index = t.index(2)      # Returns the index of n in tuple

froml = tuple(nl)             # Convert list to tuple
fromt = list(t)               # Convert tuple to list
```

### Listas (`list`)

Colección mutable y dinámica. Es la colección predeterminada y la que mayor uso tiene. Contiene gran número de métodos de manipulación y la mayor flexibilidad en su uso (reasignación, *slicing*, etc.), pero no está tan optimizada como otros tipos más limitados.

```py
l: list = [1, 2, False, "abc", 2.3, (1, 2), [3, 4, 5], {"a", 4}]
l[1] = "two"                # replace elemnent [n]
last_element = l[-1]        # get the last element 
sublist = l[3:5]            # get a sublist from n to m (not included)
from_zero = l[:6]           # get a sublist from 0 to m (not included)
from_zero_to_negative = l[:-2] # get a sublist from zero to the m to last element
sublist_with_step = l[1:5:2] # get a sublist from n to m stepping o [1, 3]
l[5:6] = []                 # Remove [n:n+m] m elements from n (included)
l[5:7] = [4, 5, 3, 2]       # Replace [n:m] elements with [...]
l[4:] = [6, 5, 4]           # Replace from [n] and insert [...]

length = len(l)             # returns a lists length
nl: list = [1, 5, 2, True, 87]
# max and ming => 0 < 10000 and a < z
max(l)  # raises error str and int cannot be calculated
vmax = max(nl)              # returns max number in list (has to be the same type)
vmin = min(nl)              # returns min number in list
nlsorted = sorted(nl)       # returns sorted list (doesn't mutate) can accept a key(lambda), and a reverse=True

print(1 in l)               # returns True if element n exists in list

# This two create a new list
ml = 2 * l                  # repeats de list n times
cl = l + nl                 # Concat

del l[2]                    # deletes l[n]
del l                       # deletes list
nl.append(3)                # appends n to end
count = nl.count(2)         # returns count of n
nl.extend(l)                # concat nl + l == nl + l
index = nl.index(2)         # returns index of n
nl.insert(2, 21)            # Injects in m in n index
poped = nl.pop()            # removes and returns last or n element
nl.remove(21)               # Remove first occurence of n
nl.reverse()                # reverses list
nl.sort()                   # sort list, key can be specified (lambda, etc), reverse=True is an option
```

> Función range(\_start, end, step). Genera una secuencia de números que van desde \_start (por defecto es 0), hasta end (requerido), con un *paso* *step*

### Sets (`set`)

Colecciones sin orden, mutables y que solo permiten valores únicos. Se comportan como claves de diccionarios sin valor. Con ellos se pueden hacer operaciones matemáticas como uniones, diferencias, intersecciones, etc.

```py
se: set = { 1, 2, 3, 4, 2, 1 }      # Removes the repeated elements
si = set(list)                      # Set from list, removes duplicates
in_set = 4 in se                    # Returns True if n exists in Set

se.add(3)                           # Add n to the Set
se.clear()                          # Eliminates Set
copy_set = se.copy()                # Returns shallow copy of Set
dis_set = se.discard(3)             # Removes n from Set. Doesn't raise exception if not found
pop_set = se.pop()                  # Removes element from Set. Not clear which
rem_set = se.remove(3)              # Removes n from Set. Raises exception if not found

# Set Operations

```

### Diccionarios (`dict`)

Colecciones de tipo clave(k), valor(v). Su sintaxis se asemeja a objetos JSON. Las claves deben ser de un tipo inmutable (números, strings o tuplas), mientras que los valores pueden ser de cualquier tipo, sea inmutable o no. Si se intenta acceder a una *k* que no existe, se genera un error *KeyError*. Para evitarlo se utiliza el método `get(key, default)`.

```py
diccionario = {
  1: "uno",
  2: "dos",
  "origen": "tu casa",
  (1, 2): 32
}

print(diccionario["nombre"])
print("origen" in diccionario) # True
print(32 in diccionario.values()) # True

del diccionario["uno"]          # Elimina n de dict
# d.clear()                     # limpia los elementos
dd = d.copy()                   # Shallow copy of dict
dg = d.get(1, "not available")  # get value with key n, or default
di = d.items()                  # returns a set-like with the k, v pair in tuples (k, v)
dk = d.keys()                   # returns a set-like with k
du = d.update()                 # no idea what this does
dv = d.values()                 # returns a set-like with v
popped_d = d.pop(1, "banana")   # Returns and deletes n (or default) from dict
from_keys = dict.fromkeys([1 ,2, 3], "halal") # Creates dict with n keys and m value

lista_diccionario = [
  {
    "nombre": "Manuel",
    "ciudad": "Málaga",
    "edad": 23
  },
  {
    "nombre": "Juan",
    "ciudad": "Jaén",
    "edad": 21
  },
  {
    "nombre": "Hidalgo",
    "ciudad": "Huelva",
    "edad": 29
  }
]

print(lista_diccionario[1]["nombre"])

for elemento in lista_diccionario:
  print(elemento["nombre"])
```
