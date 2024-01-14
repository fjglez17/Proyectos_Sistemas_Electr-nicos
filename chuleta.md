### Chuleta de control de versiones con git
Conceptos m�nimos que tenemos que saber sobre el control de versiones
CONTROL DE VERSIONES LOCAL: Es el que se realiza en una sola m�quina. Soportado por todos los sistemas de control de versiones, desde los m�s antiguos hasta los actuales. Se realiza sobre un directorio y todos sus subdirectorios.
 REPOSITORIO LOCAL (Local Repository): Es una base de datos centralizado donde se guardan las distintas versiones de los ficheros sometidos a control de versiones. 
REPOSITORIO REMOTO o REPOSITORIO o REPO (Remote repository/Repository/Repo): Es una base de datos centralizada donde se guardan las distintas versiones de los ficheros sometidos a control de versiones, y reside en el servidor centralizado (p.ej, en Github) .
COMMIT (versi�n): Cada uno de los cambios que sufre un fichero y que quedan identificados por un n�mero �nico. 
COPIA LOCAL (working copy): Es la copia que hacen los usuarios de un fichero sometido a control de versiones. El DIRECTORIO LOCAL (working directory/working tree/workspace) es el que contiene todas las copias locales.
LOG (Hist�rico): Registro de todos los cambios que se han producido en el repositorio. Es responsabilidad del cliente a�adir informaci�n al log cuando se produce un cambio.
CONFLICTO: problema que surge cuando se realizan cambios incompatibles entre s�.
SIN SEGUIMIENTO: significa que Git ve un archivo que no ten�a en la instant�nea anterior (confirmaci�n); Git no comenzar� a incluirlo en sus instant�neas de confirmaci�n hasta que le indique expl�citamente que lo haga. Hace esto para que no comience a incluir accidentalmente archivos binarios generados u otros archivos que no ten�a la intenci�n de incluir.

FICHERO CONFIRMADO (commited file): Es el fichero que ya est� almacenado en el repositorio. La �ltima versi�n y la copia local son iguales. 
FICHERO MODIFICADO (modified file): Es el fichero modificado en la copia local existe una diferencia entre la copia local y la �ltima versi�n en el repositorio. 
FICHERO PREPARADO (staged file): Es la copia del fichero modificado preparada para ser confirmada en la pr�xima operaci�n de confirmaci�n (COMMIT). La ZONA DE PREPARACI�N (staging area or index) contiene todos los ficheros preparados. 
FICHERO IGNORADO (ignored file): Es el fichero que est� en el directorio local pero que deliberadamente no se somete a control de versiones.
COMMIT(confirmar) Confirmar los ficheros preparados para su almacenamiento en el repositorio. 
CHECK-OUT Obtener una copia local descargando un fichero del repositorio. Puede ser de la �ltima versi�n o de cualquiera de las anteriores. Si se hace sobre un fichero modificado, se descartan las modificaciones sustituy�ndose por el que hab�a. 
ADD(agregar) Realiza una copia de un fichero modificado, poni�ndola en la zona de preparaci�n para poder ser confirmada. 
RESET Es el �undo� de Git. Puede descartar la copia de la zona de preparaci�n, pero tambi�n puede deshacer uno o varios commits (muy �til!) 
RESTORE Versi�n simplificada de RESET, m�s intuitiva. 
DIFF Compara versiones de ficheros. Hola flavi 
CLONE(clonar): Replica un repositorio entero con todo su historial de cambios y actualiza el directorio local 
PUSH(subir): Es la operaci�n en la que se env�an al repositorio centralizado un commit o conjunto de commits, incluido una rama entera. 
PULL(bajar): Es la operaci�n en la que se actualiza el repositorio y el directorio locales con commits que provienen del repositorio remoto. 
FETCH: Trae los commits de un repositorio remoto a un repositorio local, pero no actualiza el directorio local. Se utiliza menos que las otras.
Fork(bifurcar): clone que se hace dentro de un mismo servidor. Por ejemplo: el repositorio original y el clonado ambos residen en GitHub. Al original se le suele llamar UPSTREAM.
Pull Request(solicitud de extracci�n): petici�n que hace el desarrollador de que los cambios hechos en su repositorio clonado mediante un FORK sean incorporados al repositorio original.
Rebase (Rebasar): Rebasa la historia de una rama moviendo sus cambios a otra rama, aplicando cada commit uno tras otro.
Merge (Combinar): Combina los cambios de dos o m�s ramas en un nuevo commit de fusi�n.
Qu� tenemos que saber hacer con Git (y GitHub)

En el int�rprete de comandos de git-bash
El terminal de git-Bash funciona como cualquier terminal de Linux. Sabiendo esto consideramos que:
* Para ver en que directorio nos encontramos usamos el comando �pwd� directamente.
* Para crear un directorio: �mkdir directorio�.
* Para cambiar de directorio �cd� con la ruta directamente o usando �cd..� para ir retrocediendo en la ruta de directorios.
* Para mostrar lista de ficheros usamos el comando �ls�.
* Para borrar usamos el comando �rm nombre� y para directorios �rm -r directorio�. Remove.
* Para mover, usamos �mv nombre Destino� desde el directorio donde se encuentre el archivo.
Control de versiones LOCAL
Para crear un repositorio local usamos desde el git-Bash alguno de los siguientes comandos:
* Desde cero: Usamos git init desde el directorio donde queremos que se cree el directorio. Si queremos crearlo en un nuevo directorio especificado usamos �git init {Nombre}�.
* Desde repositorio remoto: Usamos �git clone {url_repositorio_remoto}�.
* Desde repositorio local: �git clone {ruta}.

Para ignorar ficheros creamos un archivo terminado en .gitignore donde est�n indicados espec�ficamente los archivos, directorios completos o tipo de archivo.

Para preparar ficheros para ser confirmados se puede usar �git add {ruta_archivo o nombre}�.

Tras realizar el git add, para confirmar todos los cambios usamos el comando <git commit -m �{anotaci�n nuestra}�>. 

Deshacer la operaci�n de preparar usamos git restore y el nombre del archivo (as� se recuperar� el archivo del commit del HEAD). 
Tambi�n podr�amos usar un �git reset  - -soft HEAD� para borrar los staged, es decir, aquellos archivos que hayan sido added.

El �git reset� tiene tres niveles:
* �- -soft�: Borra los staged del HEAD o los que indiquemos {ID commit}.
* �- -mixed�: Borra los staged y committed del HEAD.
* �- -hard�: Borra TODO lo que haya despu�s de dicho commit.

Para identificar el estado de un fichero o ficheros del repositorio usaremos �git status�. Los cambios se ver�an en distintos colores dependiendo si est�n modificados, preparados o confirmados.

Crear una rama en un repositorio local, se puede hacer:
* �git Branch {nueva rama}�. Tambi�n se puede usar �git Branch� para listar todas las ramas o borrarlas con �git Branch -d {nombre de la rama}�.
* �git checkout -b {nueva_rama}� todo esto es para hacerlo a partir del HEAD, pero se puede hacer una rama nueva a partir de otra nueva rama: �git checkout -b {nueva rama} {rama origen}�.
Para cambiar de rama podemos usar:
* �git checkout {nombre de la rama}� OJO que aqu� tambi�n se hace un restore, es decir, que restaura los archivos a los que vamos.
* �git switch {nombre de la rama}�. Aqu� solo cambia la rama sin restaurar los archivos del destino.
Fundir los cambios de una rama en otra podemos usar:
Merge: Se fusiona un commit adicional en la rama que queramos.
Para injertar una rama en otra se utiliza:
�git rebase {
nombre de la rama}� Mueve los cambios no los combina en un nuevo commit.


Comandos interesantes: 
�git diff {commit1}{commit2}� : Lista las diferencias entre los archivos de dos commits distintos.

************En Remoto************

�	Configurar git para que trabaje tras un proxy: 
para http
git config --global http.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
para https
git config --global https.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
para deshabilitar el uso del proxy
git config --global --unset http.proxy
�	nombre de usuario: nombre de usuario para autenticarse en el servidor de proxy.
�	password: password para identificarse en el servidor proxy.
�	direccion_ip: direcci�n de servidor de proxy.
�	puerto: en el que est� escuchando el servidor proxy.


�	Replicar un repositorio remoto localmente en nuestra m�quina.
git clone <repo url>
El comando git clone se usa para crear una copia o clonar un repositorio remoto. Se utiliza git clone con la URL de un repositorio. Git es compatible con varios protocolos de red y sus formatos de URL correspondientes.
Ej: git clone https://github.com/usuario/repo.git

�	Replicar un repositorio local en un servidor remoto.
Para replicar un repositorio local en un servidor remoto en Git, sigue los siguientes pasos:
1.	A�ade el servidor remoto a tu repositorio local utilizando el comando git remote add [nombre] [url]. Por ejemplo, si el nombre del servidor remoto es origin y la URL es https://github.com/usuario/repositorio.git, el comando ser�a git remote add origin https://github.com/usuario/repositorio.git.
2.	Verifica que el servidor remoto se ha a�adido correctamente utilizando el comando git remote -v.
3.	Empuja los cambios de tu repositorio local al servidor remoto utilizando el comando git push [nombre] [rama]. Por ejemplo, si el nombre del servidor remoto es origin y la rama es master, el comando ser�a git push origin master.

�	Traer los cambios de un repositorio remoto a un repositorio local.
Para traer los cambios al repositorio local usaremos el comando git fetch [nombre servidor]

�	Resolver los conflictos que se puedan producir al traerse estos cambios.
 Buscando \<\<\<\<\<\<\<, ======= y \>\>\>\>\>\>\> y editando el archivo manualmente con los cambios deseados.

�	Enviar los cambios de un repositorio local a uno remoto.
git push origin <branch>

�	Enviar una rama local al repositorio remoto de manera que la local quede enganchada (haga tracking de) la remota.
Utilizaremos el siguiente comando: git push -u \<rama remota\> \<rama local\>

�	Incorporar a ramas locales cambios que se producen en el repositorio remoto.
1.	Descarga los cambios del servidor remoto a tu repositorio local utilizando el comando git fetch [nombre]. Por ejemplo, si el nombre del servidor remoto es origin, el comando ser�a git fetch origin.
2.	Combina los cambios descargados en tu repositorio local utilizando el comando git merge [nombre]/[rama]. Por ejemplo, si la rama es master, el comando ser�a git merge origin/master.
3.	Si hay conflictos, Git te notificar� que hay conflictos sin resolver. Abre los archivos en conflicto y resuelve los conflictos manualmente utilizando el comando git mergetool. Si no tienes un programa de fusi�n configurado, puedes resolver los conflictos manualmente editando los archivos en conflicto.

�	Crear un repositorio remoto vac�o.
  Para crear un repositorio remoto, le daremos a la opci�n  de new en nuestro men� de github, posteriormente le pondremos un nombre y elegiremos si es p�blico o privado. Por �ltimo, le daremos a Create repository.

�	Invitar a colaboradores.
  Para invitar colaboradores pulsaremos en invite collaborators y a continuaci�n en add people poniendo el nombre de los usuarios o correos a los que quieres invitar.

�	Realizar un pull request entre dos ramas de un repositorio remoto.
 Si vas a tu repositorio veras un bot�n llamado pull request, haz click en �l.

�	Realizar un pull request entre dos repositorios que resultaron de un Fork.
De la misma manera que anteriormente, iremos a nuestro repositorio y pulsaremos en el bot�n pull request.
