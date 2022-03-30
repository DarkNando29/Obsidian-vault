[[Git Basic Base]]

## Que es?
Es una copia de algun punto de la historia de master (normalmente) o de otra rama


### Como crear un branch
> git branch 'Name' 
> Con este commando podemos crear una nueva rama en nuestro local.

> git branch
> Con este comando enlistaremos todas las ramas en nuestro local.

>git show-branch
>Con este comando enlistariamos todos los branch con sus commits.

>git checkout 'branchName'
>Nos movemos a otra rama segun el nombre especificado.

>git checkout -b 'branchName
>Con este comando crearemos una nueva rama y nos moveremos a ella directamente.'

#### Fusionar ramas (merge)
>git merge 'branchName'
>Fusiona la rama especificada dentro de la rama en la que te encuentras.

>git merge 'branchName' -m 'Esto es un merge con mensaje'
>Fusionar una rama necesitara un msj con el atributo o parametro -m

>git merge master -m 'Un mensaje del merge de master en el branch experimental'
>Fusionar una rama master con la rama en la que estas posicionado.

#### Subir ramas a repositorio remoto(push)
>git push -u origin 'branchName'

#### Eliminar una rama(-d o -D)
>git branch -d 'branchName'
>git branch -D 'branchName'
>Estos dos commandos eliminan la rama, pero a diferencia del primero, el segundo fuerza el borrado.

>git push origin --delete rama_a_borrar
>Este comando elimina el repositorio remoto.

#### Descargar una rama del remoto
##### Primeramente actualizamos el repo
>git fetch
>Tomamos la actualizacion del remoto.

>git checkout 'branchName'
>Nos movemos a la rama descargada.

### Beneficios de crear una rama
-Aqui es donde esta todo el beneficio de Git como sistema de control de versiones, al crear una rama la version de master esta completamente separa de los cambios que vayas a hacer en tu rama, no hay problema si quieres experimentar en tu rama, editar partes, por que la principal y la que se usa para todo es master.

#### Comandos utiles para los branch

> git reset "tag" --hard 
> Borra todo. Todo todito, absolutamente todo. Toda la información de los commits y del área de staging se borra del historial.

> git reset "tag" --soft
> Borramos todo el historial y los registros de Git pero guardamos los cambios que tengamos en Staging, así podemos aplicar las últimas actualizaciones a un nuevo commit.. 

> git checkout "tag o nombre de branch" "file"
> Dentro de la git tomamos un commit especifico (indicado por el tag) y lo ponemos en nuestro disco duro.
> Al hacer un checkout de una rama sin especificar el archivo me trae toda la rama a mi disco duro.

> git rm --cached: 
> Elimina los archivos de nuestro repositorio local y del área de staging, pero los mantiene en nuestro disco duro. Básicamente le dice a Git que deje de trackear el historial de cambios de estos archivos, por lo que pasaran a un estado untracked.


> git rm --force: 
> Elimina los archivos de Git y del disco duro. Git siempre guarda todo, por lo que podemos acceder al registro de la existencia de los archivos, de modo que podremos recuperarlos si es necesario (pero debemos usar comandos más avanzados).