### Chuleta de control de versiones con git

En el intérprete de comandos de git-bash
El terminal de git-Bash funciona como cualquier terminal de Linux. Sabiendo esto consideramos que:
* Para ver en que directorio nos encontramos usamos el comando “pwd” directamente.
* Para crear un directorio: “mkdir directorio”.
* Para cambiar de directorio “cd” con la ruta directamente o usando “cd..” para ir retrocediendo en la ruta de directorios.
* Para mostrar lista de ficheros usamos el comando “ls”.
* Para borrar usamos el comando “rm nombre” y para directorios “rm -r directorio”. Remove.
* Para mover, usamos “mv nombre Destino” desde el directorio donde se encuentre el archivo.
Control de versiones LOCAL
Para crear un repositorio local usamos desde el git-Bash alguno de los siguientes comandos:
* Desde cero: Usamos git init desde el directorio donde queremos que se cree el directorio. Si queremos crearlo en un nuevo directorio especificado usamos “git init {Nombre}”.
* Desde repositorio remoto: Usamos “git clone {url_repositorio_remoto}”.
* Desde repositorio local: “git clone {ruta}.

Para ignorar ficheros creamos un archivo terminado en .gitignore donde estén indicados específicamente los archivos, directorios completos o tipo de archivo.

Para preparar ficheros para ser confirmados se puede usar “git add {ruta_archivo o nombre}”.

Tras realizar el git add, para confirmar todos los cambios usamos el comando <git commit -m “{anotación nuestra}”>. 

Deshacer la operación de preparar usamos git restore y el nombre del archivo (así se recuperará el archivo del commit del HEAD). 
También podríamos usar un “git reset  - -soft HEAD” para borrar los staged, es decir, aquellos archivos que hayan sido added.

El “git reset” tiene tres niveles:
* “- -soft”: Borra los staged del HEAD o los que indiquemos {ID commit}.
* “- -mixed”: Borra los staged y committed del HEAD.
* “- -hard”: Borra TODO lo que haya después de dicho commit.

Para identificar el estado de un fichero o ficheros del repositorio usaremos “git status”. Los cambios se verían en distintos colores dependiendo si están modificados, preparados o confirmados.

Crear una rama en un repositorio local, se puede hacer:
* “git Branch {nueva rama}”. También se puede usar “git Branch” para listar todas las ramas o borrarlas con “git Branch -d {nombre de la rama}”.
* “git checkout -b {nueva_rama}” todo esto es para hacerlo a partir del HEAD, pero se puede hacer una rama nueva a partir de otra nueva rama: “git checkout -b {nueva rama} {rama origen}”.
Para cambiar de rama podemos usar:
* “git checkout {nombre de la rama}” OJO que aquí también se hace un restore, es decir, que restaura los archivos a los que vamos.
* “git switch {nombre de la rama}”. Aquí solo cambia la rama sin restaurar los archivos del destino.
Fundir los cambios de una rama en otra podemos usar:
Merge: Se fusiona un commit adicional en la rama que queramos.
Para injertar una rama en otra se utiliza:
“git rebase {
nombre de la rama}” Mueve los cambios no los combina en un nuevo commit.


Comandos interesantes: 
“git diff {commit1}{commit2}” : Lista las diferencias entre los archivos de dos commits distintos.
