[[Git Basic Base]]

#### Comandos de creacion del repositorio.
git init: 
	Iniciar un repo en la carpeta que se escogio
git status: 
	- Estado del repositorio.
	- En este comando se analizan cambios que han sucedido en todo el repositorio que ha cambiado y que no, recordemos que git tiene diferentes areas de trabajo, y la primera que se utiliza es la local.
git rm --cached "File":
	- Elimina el "archivo" pero realmente lo que esta haciendo es eliminar el tracked que esta haciendo sobre ese cambio. 
	
git add "File":
- Agrega el archivo o directorio indicado para que sea trackeado por git, para agregar sus cambios. 

git commit -m "Details about the changes":
- Se crea un commit con todos los cambios agregados en el stage area [[Stages and unstage]]
	
	
	
#### Settings 
git config --list: 
- Lista de todos los settings que se tienen para git.

git config --list --show-origin:
- Lista de todos los settings que se tienen para git (con sus directorio de origen)

git config --global user.email "tu@email.com"
- Comando para configurar los settings personales (correo)

git config --global user.name "Tu Nombre"
- Comando para configurar los settings personales (nombre)
	