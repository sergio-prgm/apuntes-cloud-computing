# Día 8

## Código Limpio y Refactorización (módulo 10)

Estándares de código y normalización.

Refactorización (deuda técnica, testing)

Agile manifesto.

Scrum y Kanban

* Product Owner: anota historias, las añade al backlog y estima el tiempo de implementación.

TDD (noooooooo)

## Gestión de version y Git

Repositorio: almacenamiento físico y lógico de la info. Contiene la historia del código y las distintas ramas *branch*.

Versionado: cada aportación tiene un id único para poder recuperarlo.

Colaboración: permite desarrollar de manera simultánea y organizada.

Branch: línea separada con su propia historia. Permite desarrollo y modificación más seguro al ser independiente del resto. Siempre debe haber una *master*

Para incorporar los contenidos de una rama a otra se hace *merge* o *rebase*. En general es mejor usar *merge* a la hora de incorporar cambios a *master*, pues mantiene los *logs* (metainformación sobre los commits y los cambios) y usar *rebase* para incorporar cambios en ramas no principales.

Commit: cada hito en el proceso de desarrollo en el que hay ciertor cambios se conoce como commit. No hay reglas sobre su extensión, pero en general lo mejor es que sea lo más mínimo y expresivo posible, es decir, que los cambios tengan un enfoque claro.

URL:

.gitignore: archivo que se usa para evitar incluir ciertos archivos/carpetas al seguimiento.

Iniciar repositorio de git en una carpeta:

```console
git init
```

Añadir archivos/carpetas al seguimiento/

Añadir todos los ficheros al seguimiento:

```console
git add [fichero] ó [carpeta]

git add -A
# ó
git add .
```

Revisar el estado de los contenidos de la carpeta/repositorio y de los commits/ramas:

```console
git status
git log --oneline
```

Revisar la configuración global y local de Git (lo que sale entre [] hay que ponerlo entre "" si hay espacios dentro). `-l` sirve para listar las opciones:

> No es necesario especificar configuración local si va a ser igual que la global.

```console
git config --global user.email [email]
git config --global user.name [name]
git config --global user.name Sergio
git config --global user.name "Sergio Esteve"

git config --global -l
git config --local -l
```

Hacer commit con mensaje (siempre poner un mensaje lo más descriptivo posible):

```console
git commit -m "[mensaje]"
```

Hacer commit y añadir todos los archivos al seguimiento:

```console
git commit -m "[mensaje]" -a
```

Usar *tags*. Estas se usan generalmente para diferenciar versiones, p.e.: "v1.0.2". Si la etiqueta debe estar en el commit actual no hace falta especificar el `[id commit]`:

```console
git tag [tag] [id commit]
```

Crear una rama y cambiar a ella. Todas las ramas se crean a partir del commit en el que se encuentra:

```console
git checkout -b [nombre de la rama]
git switch -c [nombre de la rama]
```

Regresar a un estado anterior o posterior:

```console
git checkout [id o nombre commit]
git checkout -
```

Diferencia entre checkout y switch

Mergear los cambios de una rama a otra. Posicionarse en la rama de destino:

```console
git chekcout [rama destino]
git merge [rama de cambios]
```

Ahora los commits que se hayan hecho en la rama alternativa se han unido (fusionado) a la rama destino como si se hubieran realizado en esa misma.

```console
git diff [rama origen] [rama destino]
git diff --base [fichero]
git diff
```
