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

************En Remoto************

•	Configurar git para que trabaje tras un proxy: 
para http
git config --global http.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
para https
git config --global https.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
para deshabilitar el uso del proxy
git config --global --unset http.proxy
•	nombre de usuario: nombre de usuario para autenticarse en el servidor de proxy.
•	password: password para identificarse en el servidor proxy.
•	direccion_ip: dirección de servidor de proxy.
•	puerto: en el que está escuchando el servidor proxy.


•	Replicar un repositorio remoto localmente en nuestra máquina.
git clone <repo url>
El comando git clone se usa para crear una copia o clonar un repositorio remoto. Se utiliza git clone con la URL de un repositorio. Git es compatible con varios protocolos de red y sus formatos de URL correspondientes.
Ej: git clone https://github.com/usuario/repo.git

•	Replicar un repositorio local en un servidor remoto.
Para replicar un repositorio local en un servidor remoto en Git, sigue los siguientes pasos:
1.	Añade el servidor remoto a tu repositorio local utilizando el comando git remote add [nombre] [url]. Por ejemplo, si el nombre del servidor remoto es origin y la URL es https://github.com/usuario/repositorio.git, el comando sería git remote add origin https://github.com/usuario/repositorio.git.
2.	Verifica que el servidor remoto se ha añadido correctamente utilizando el comando git remote -v.
3.	Empuja los cambios de tu repositorio local al servidor remoto utilizando el comando git push [nombre] [rama]. Por ejemplo, si el nombre del servidor remoto es origin y la rama es master, el comando sería git push origin master.

•	Traer los cambios de un repositorio remoto a un repositorio local.
Para traer los cambios al repositorio local usaremos el comando git fetch [nombre servidor]

•	Resolver los conflictos que se puedan producir al traerse estos cambios.
 Buscando \<\<\<\<\<\<\<, ======= y \>\>\>\>\>\>\> y editando el archivo manualmente con los cambios deseados.

•	Enviar los cambios de un repositorio local a uno remoto.
git push origin <branch>

•	Enviar una rama local al repositorio remoto de manera que la local quede enganchada (haga tracking de) la remota.
Utilizaremos el siguiente comando: git push -u \<rama remota\> \<rama local\>

•	Incorporar a ramas locales cambios que se producen en el repositorio remoto.
1.	Descarga los cambios del servidor remoto a tu repositorio local utilizando el comando git fetch [nombre]. Por ejemplo, si el nombre del servidor remoto es origin, el comando sería git fetch origin.
2.	Combina los cambios descargados en tu repositorio local utilizando el comando git merge [nombre]/[rama]. Por ejemplo, si la rama es master, el comando sería git merge origin/master.
3.	Si hay conflictos, Git te notificará que hay conflictos sin resolver. Abre los archivos en conflicto y resuelve los conflictos manualmente utilizando el comando git mergetool. Si no tienes un programa de fusión configurado, puedes resolver los conflictos manualmente editando los archivos en conflicto.

•	Crear un repositorio remoto vacío.
  Para crear un repositorio remoto, le daremos a la opción  de new en nuestro menú de github, posteriormente le pondremos un nombre y elegiremos si es público o privado. Por último, le daremos a Create repository.

•	Invitar a colaboradores.
  Para invitar colaboradores pulsaremos en invite collaborators y a continuación en add people poniendo el nombre de los usuarios o correos a los que quieres invitar.

•	Realizar un pull request entre dos ramas de un repositorio remoto.
 Si vas a tu repositorio veras un botón llamado pull request, haz click en él.

•	Realizar un pull request entre dos repositorios que resultaron de un Fork.
De la misma manera que anteriormente, iremos a nuestro repositorio y pulsaremos en el botón pull request.
