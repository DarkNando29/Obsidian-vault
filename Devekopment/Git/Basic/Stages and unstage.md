[[Git Basic Base]]

#### Staged area:
> Area en la que se agregan todos los cambios que sabemos y estamos seguros de compartir y agregar al proyecto.

#### Unstaged area:
> Area en la que se registran todos los cambios dentro del repositorio, archivo por archivo.

## Ciclo basico de Git
- Al hacer un cambio en un archivo git primeramente no va a tomar esto en cuenta, pero si sabra que se hicieron cambios en el de la siguiente manera.

| Directorio | Staging | Repo Local |
| ---------- | -------- | ----- | 
 | file1.txt | | | 
 
 -  Una vez que hagamos el comando git add, agregaremos los datos para que pasen a ser trackeados por el staging.
 
 | Directorio | Staging | Repo Local |
| ---------- | -------- | ----- | 
 | file1.txt | file1.txt | | 
 
- Cuando hacemos commit preparamos un paquete, un paquete que se creara con todo lo que este en el staging area,  se movera al repositorio.

| Directorio | Staging   | Repo Local      |
| ---------- | --------  | -----     | 
| file1.txt  | file1.txt | file1.txt | 