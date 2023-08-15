# Prácticas

## Práctica 1: Setup del proyecto
En esta práctica el alumno realizará los pasos necesarios para contar con el proyecto de Software que se utilizará durante el ciclo.

### Pre-requisitos
1. Contar con su cuenta de Github y estar agregado al repositorio
2. Tener instalado un cliente de Git en su máquina
3. Tener registrada su clave SSH en Github
4. Tener Node y Yarn instalados
5. Tener un editor de código de su preferencia (VSCode, IntelliJ, etc..)

### Pasos
1. Abrir una terminal de su preferencia (Gitbash, Powershell, etc.)
2. Crear una carpeta donde se guardaran los proyectos de la materia
   ```
   mkdir -p ~/projects/tecnologico/estandares-de-calidad
   cd ~/projects/tecnologico/estandares-de-calidad
   ```
3. Clonar el proyecto
   ```
   git clone git@github.com:EstandaresDeCalidadSW23/amiguitosvisibles.git
   cd amiguitosvisibles
   ```
4. Instalar dependencias y correr el proyecto
   ```
   yarn install
   yarn dev
   ```
5. Abrir el navegador de preferencia e ir a la Url que nos muestra la salida del comando anterior (http://localhost:3000)
6. Revisar que el proyecto funcione correctamente.

## Práctica 2: Agregarse como Colaborador del proyecto
En esta práctica, el estudiante comprobará que puede realizar cambios en el proyecto, a tráves de crear nuevas ramas y utilizar Pull Requests.

### Pre-requisitos
1. Realizar Práctica 1

### Pasos
1. Crear una rama a partir de la rama `master` con el siguiente formato `nombre-practica-2`. Ejemplo:
   ```
   git checkout master
   git pull origin master
   git branch benjamin-practica-2
   git checkout benjamin-practica-2
   ```
2. Abrir el archivo README.md e ir a la sección Collaborators y agregar su nombre/usuario a la lista. Ejemplo:
   ```
   ## Collaborators
   - Benjamin Cisneros - @bcisneros
   ```
3. Realizar un commit y push del proyecto
   ```
   git add README.md
   git commit -m "Se agrega Benjamin Cisneros a la lista de colaboradores"
   git push --set-upstream origin benjamin-practica-2
   ```
4. Crear un nuevo Pull Request en Github (https://github.com/EstandaresDeCalidadSW23/amiguitosvisibles/pull/new/TU_BRANCH)
   > ℹ️ Nota: Reemplazar TU_BRANCH por el nombre de tu branch
5. Agregar a Benjamin Cisneros y Carlos Moriel como Revisores y agregar una pequeña descripción en el Pull Request.
6. Esperar a que el Pull Request sea aprobado y hacer Merge a master desde el Pull Request.
