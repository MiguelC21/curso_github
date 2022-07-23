# Curso de Git y GitHub

Curso avanzado de **git** y **github** en el que aprendimos lo siguiente:

- Comandos básicos para repositorios locales
- Comandos para el manejo de repositorios remotos
- Creación de tags y versiones
- Colaboración en proyectos públicos open source con Fork
- Ver interfaz gráfica de git
- Solución de errores mas comunes
- Comandos y recursos colaborativos
- Creación de alias para grupos de comandos
- Obtener ayuda en linea a cerca de los comandos
- Agregas exclusiones de seguimiento de archivos con .gitignore

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSrQc0ANPZWnN4taq9ovVf34p26a23iBIeHNQ&usqp=CAU)

------------

## LISTA DE COMANDOS PARA TRABAJAR CON GIT  GITHUB
###### Para iniciar git en un proyecto (ésta acción se realiza una vez por proyecto):
`git init`

###### Antes de continuar vamos a configurar nuestro nombre y email, para ello ejecutamos el comando
`git config --global user.name 'tu nombre'`
`git config --global user.email 'tu@email.com'`


------------

#### COMANDOS BÁSICOS DE GIT
- `git init`           // Inicia un repositorio local.
- `git add .`         // Añade los ficheros al Seguimiento.
- `git status -s`    // Comprueba el estado de seguimiento de archivos stalling.
- `git commit -m`    // Commit los cambios.
- `git branch nombreRama` //Crear una nueva rama.
- `git branch -m nombreRama nombreNuevo` //Cambiar el nombre de una rama.
- `git branch -d nombreRama` // Borrar rama (solo ramas ya fusionadas).
- `git branch -D nombreRama` // Borrar rama sin importar si no ha sido fusionada aun.
- `git branch` // Ver la rama en la que estoy y las ramas locales.
- `git branch -a` // Ver la rama en la que estoy y las ramas en el repositorio remoto.
- `git branch -r` // Ver las ramas del repositorio remoto.
- `git branch -M nombreRama` // Selecciona la rama en la que se quiere trabajar.


#### PARA TRABAJAR CON REPOSITORIOS REMOTOS
- `git remote add origin url` // Dirección del git
- `git pull --rebase origin main` // Combinar los repositorios por primera vez
- `git push origin nombreRama` // Enviar nuestros cambios al repositorio remoto
- `git pull origin nombreRama` // Descarga los últimos cambios del repositorio remoto
- `git clone 'url o ssh'` // Clona, o realizar una copia desde el repositorio remoto al local para repositorios que ya contienen archivos.
- `git checkout nombreRama` // Movernos entre ramas
- `git merge nombreRamaAFusionar` // Fusionar la rama actual con la rama que acabamos de nombrar
###### ...Hacer FORK
- `git remote add upstream url del proyecto al que se le hizo un fork` // (La palabra upstream es opcional. puede ser cualquier cosa) Este comando se utiliza para poder traer los datos de la fuente original del proyecto a nuestro proyecto local furkeado.
- `git remote  -v` // Miramos las fuentes de datos de donde podemos traer los cambios a nuestro proyecto


#### PARA EL MANEJO DE TAGS
- `git tag -a nombreTag -m "mensaje" numeroCommit` // Agregamos un tag a un commit.
###### Ejemplo: git tag -a v0.1 -m "Esta es la primera version del proyecto" 6b54895
- `git tag` // Nos muestra los tag que hemos creado.
- `git tag show-ref` // Nos muestra los tags y los commits a los que están asociados.
- `git tag -d nombreTag` //Eliminamos el tag en el repositorio local.
- `git push origin --tags` //Subimos nuestros tags al repositorio remoto.
- `git pull origin --tags` //Trae los tags del repositorio remoto.
- `git push origin :refs/tags/nombreTag` //Eliminamos el tag del repositorio remoto.


#### PARA VER UNA GRÁFICA EXTERNA DE GIT
- `gitk` // Nos abre una interfaz externa donde nos muestra gráficamente la historia de nuestro proyecto.


#### SOLUCIÓN DE ERRORES
- `git rebase nombreRama` // sirve para fusionar 2 ramas pero sin dejar rastros (se debe hacer primero rebase a la rama que se quiere fusionar y luego en la rama original o de destino).
- `git stash` // Sirve para volver al estado anterior al que estábamos antes de modificar un archivo al que no hemos agregado al stalling.
- `git stash list` // Me permite ver la lista de copias de stash de WIP (Work In Progress) al que le hice stash
- `git stash pop` // Me devuelve los cambios que tenia en WIP.
- `git stash branch nombreRama` // podemos llevarnos lo que tenemos en stash a una nueva rama.
- `git stash drop` // borro la lista de stash.
- `git clean --dry-run` //Este comando nos muestra la lista de archivos que hallamos duplicado por error en nuestro repositorio a excepción de carpetas y archivos que estén dentro de gitignore.
- `git clean  -f` // Nos borra la lista de archivos duplicados que se muestran con el comando anterior
- `git cherry-pick numeroCommit` // Nos sirve para agregar un commit en especifico de una rama a otra.
- `git reflog` // Nos muestra el historial de absolutamente todo lo que hemos realizado en git (Podemos regresar a cualquiera de punto del historial haciendo un git reset --hard numeroCommit).
- `git commit --amend -m"nombrarCommit"` // Agregas cambios nuevos al ultimo commit que subí.
- `git grep palabraABuscar` // Nor permite buscar una palabra en todo nuestro repositorio (solo los busca en la rama que estemos actualmente).
- `git grep -n palabraABuscar` // Nor permite buscar una palabra en todo nuestro repositorio con la linea y el archivo en que se encuentra.
- `git grep -c palabraABuscar` // Nos cuenta el total y el numero de veces que se encuentra la palabra en nuestro repositorio.
- `git log -S "palabraABuscar"` // Busca resultados de la palabra asociados a nuestros commits.


#### COMANDOS Y RECURSOS COLABORATIVOS
- `git shortlog` // Nos muestra la lista de personas que a trabajado en el proyecto y los commits que a realizado.
- `git shortlog -sn` // Nos muestra el numero de commits que a realizado uns persona incluyendo merges.
- `git shortlog -sn --all` // Nos muestra el numero total de commits realizados por cada uno de los integrantes del equipo incluidos los que aya borrado.
- `git git shortlog -sn --all --no-merges` // Muestra lo mismo que la lista anterior pero sin incluir los merges.
- `git blame -c nombreArchivo` // Nos muestra las modificaciones que a tenido un archivo y las personas que lo modificaron.
- `git blame nombreArchivo -L numeroLinea, numeroLinea -c` // Nos muestra solo las modificaciones que tuvo el archivo en el rango de lineas marcadas.


#### CREAR ALIAS PARA UN GRUPO DE COMANDOS
- `git config --global alias.nombreAlias "Comandos a llamar(sin incluir la palabra git)"` //Creamos un alias para una serie de comandos la cual podemos llamar de la siguiente manera: git nombreAlias.

#### OBTENER AYUDA
- `git nombreDelComando --help` // Nos muestra una ayuda del comando que pongamos.

------------
#### IGNORAR ARCHIVOS DE NUESTRO REPOSITORIO
Para hacer que git nos ignore un archivo del proyecto debemos crear el archivo ***.gitignore***. Luego de crearlo lo abrimos y agregamos la ruta del archivo que queremos que git nos ignore.

------------

------------

------------

