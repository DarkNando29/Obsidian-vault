[[Bases de git]]

#### Vamos a trackear nuestros cambios
1. git log "file":
	-	vamos a ver todos los cambios referentes al archivo especificado, en la historia del repositorio.
	-	Informacion que vamos a ver:
		-	Commit "tag":
			-	identificador del commit en el que se hizo un cambio especifico al archivo
		-	Author:
			- Autor del cambio especifico en el archivo.
		-  Date:
			-  Fecha en la que se realizo el cambio. 

2. git log --stat :
	- Cambios 

3. git show "file":
	-  Detalles especificos que se dieron en el file.

4. git diff "tag" "tag":
	- Comparo los diferentes commits segun su tag

5.  git log --oneline - Te muestra el id commit y el título del commit.
6.  git log --decorate- Te muestra donde se encuentra el head point en el log.
7.  git log --stat - Explica el número de líneas que se cambiaron brevemente.
8.  git log -p- Explica el número de líneas que se cambiaron y te muestra que se cambió en el contenido.
9.  git shortlog - Indica que commits ha realizado un usuario, mostrando el usuario y el titulo de sus commits.
10.  git log --graph --oneline --decorate y
11.  git log --pretty=format:"%cn hizo un commit %h el dia %cd" - Muestra mensajes personalizados de los commits.
12.  git log -3 - Limitamos el número de commits.
13.  git log --after=“2018-1-2” ,
14.  git log --after=“today” y
15.  git log --after=“2018-1-2” --before=“today” - Commits para localizar por fechas.
16.  git log --author=“Name Author” - Commits realizados por autor que cumplan exactamente con el nombre.
17.  git log --grep=“INVIE” - Busca los commits que cumplan tal cual está escrito entre las comillas.
18.  git log --grep=“INVIE” –i- Busca los commits que cumplan sin importar mayúsculas o minúsculas.
19.  git log – index.html- Busca los commits en un archivo en específico.
20.  git log -S “Por contenido”- Buscar los commits con el contenido dentro del archivo.
21.  git log > log.txt - guardar los logs en un archivo txt