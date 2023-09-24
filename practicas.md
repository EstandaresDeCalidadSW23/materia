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

1. Abrir una terminal de su preferencia (GitBash, Powershell, etc.)
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

En esta práctica, el estudiante comprobará que puede realizar cambios en el proyecto, a traves de crear nuevas ramas y utilizar Pull Requests.

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

## Práctica 3: Pruebas Unitaria Básicas

En esta práctica el alumno creará pruebas unitarias básicas con el lenguaje Javascript y utilizando la librería Jest.

### Pre-requisitos

1. Tener instalado Node y NPM
2. Tener instalado Git
3. Tener instalado un editor de código como VS Code

### Pasos

1. Abrir una terminal
2. Moverse a la carpeta de los proyectos destinada. Ejemplo:

```
cd ~/projects
```

3. Crear una nueva carpeta con el nombre `unit-test-kata`

```
mkdir unit-test-kata && cd unit-test-kata
```

4. Verificar que se tenga instalado Node

```
node --version
npm --version
```

5. Inicializar proyecto de Git

```
git init
```

5. Inicializar proyecto de NPM

```
npm init
```

6. Nos va a preguntar algunas configuraciones, quedando de la siguiente manera

- package name: dejamos el valor por defecto y damos Enter
- version: dejamos el valor por defecto
- description: Podemos dejar el valor por defecto o agregar una descripción breve. Ejemplo: `Pruebas Unitarias`
- entry point: dejamos el valor por defecto
- test command: `jest`
- git repository: dejamos el valor en blanco
- keywords: podemos dejar el valor en blanco o agregar algunas. Ejemplo: `tests` , `tdd`, etc..
- author: ponemos nuestro nombre
- license: dejamos el valor por defecto

7. Nos va a mostrar una confirmación a lo cual solo escribimos la palabra `yes` y damos Enter.

```
{
  "name": "unit-test-kata",
  "version": "1.0.0",
  "description": "Pruebas Unitarias",
  "main": "index.js",
  "scripts": {
    "test": "jest"
  },
  "keywords": [
    "test",
    "tdd"
  ],
  "author": "Benjamin Cisneros",
  "license": "ISC"
}


Is this OK? (yes)
```

8. Instalar la dependencia de Jest

```
npm install --save-dev jest
```

9. Ignoramos la carpeta de dependencias en Git

```
echo "node_modules/" > .gitignore
```

10. Creamos las carpetas y archivos necesarios

```
mkdir src
touch src/hello.js
mkdir test
touch test/hello.test.js
```

11. Abrimos nuestra carpeta en cualquier editor disponible. Ejemplo VS Code:

```
code .
```

12. En el archivo `src/hello.js` escribimos el siguiente código:

```js
function hello(name = "World") {
  return "Hello " + name + "!";
}

module.exports = hello;
```

13. En el archivo `test/hello.test.js` escribimos el siguiente código:

```js
const hello = require("../src/hello");

test("should say hello to given name", function () {
  // setup
  const name = "Benjamin";

  // execute
  const result = hello(name);

  // expectations
  expect(result).toEqual("Hello Benjamin!");
});
```

14. En la terminal, ejecutamos el siguiente comando:

```
npm test

> unit-test-kata@1.0.0 test
> jest

 PASS  test/hello.test.js

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.451 s
Ran all test suites.
```

15. Creamos un commit de los cambios

```
git status
git add .
git commit -m "Se agrega función hello y primer prueba unitaria"
```

16. Agregamos una nueva prueba unitaria al final del archivo `test/hello.test.js`:

```js
// ... other code

test("should say 'Hello World!' when no name is provided", function () {
  // setup
  const expected = "Hello World";

  // execute
  const result = hello();

  // expectations
  expect(result).toEqual(expected);
});
```

17. Volvemos a correr el comando `npm test` en la terminal y comprobamos que nuestros tests corren sin problemas.

18. Agregamos nuestros cambios a Git:

```
git status
git add .
git commit -m "Se agrega prueba unitaria para escenario de hello sin parámetros"
```

19. Agregar un nuevo escenario para probar otro nombre, probar y hacer commit.

## Práctica 4: Introducción a Test Driven Development (TDD)

En esta práctica el alumno construirá una funcionalidad dada utilizando la técnica de desarrollo llamada Test Driven Development, la cual se fundamenta en la creación de pruebas unitarias antes de construir cualquier código de producción.

### Definición del Problema a resolver

Se requiere contar con una función que nos permita conocer el tiempo que un proceso ha durado, de una forma que sea fácilmente legible para el usuario.

Los datos del proceso son entregados en segundos, los cuales son números enteros positivos, incluyendo el 0 (cero).

El valor de retorno de la función debe ser una cadena de texto que representa la duración de dicho proceso, con el siguiente formato:

- `[0-59]` segundos. Regresar el número de segundos: `"0s"`, `"1s"`, `"2s"`, ..., `"59s"`
- `[1-59] * 60` segundos. Regresar el número de minutos: `"1m"`, `"2m"`, `"3m"`, ..., `"59m"`
- `[1-23] * 3600` segundos. Regresar el número de horas `"1h"`, `"2h"`, `"3h"`, ..., `"23h"`
- `[1-6] * 3600 * 24` segundos. Regresar el número de días: `"1d"`, `"2d"`, `"3d"`, ..., `"23h"`
- `[n > 0] * 3600 * 24 * 7` segundos. Regresar el número de semanas: `"1w"`, `"2w"`, `"3w"`, etc...
- `[n > 0] * 3600 * 24 * 365` segundos. Regresar el número de años: `"1y"`, `"2y"`, `"3y"`, etc...

En el caso de el número ingresado no sea múltiplo de los valores mencionados, deberá regresarse las unidades consecutivas.

Ejemplo:

```js
// 3600 (1 hora) + 360 (6 minutos) + 18 (segundos)
time(3600 + 360 + 18);

// salida: "1h 6m 18s"
```

En el caso de que no exista la unidad consecutiva solamente se debe mostrar hasta la primer unidad completa.

Ejemplos:

```js
// Ejemplo 1
// 2 años (en segundos) + 5 días (en segundos) + 3 horas (en segundos)
const HOURS_IN_SECONDS = 3600;
const DAYS_IN_SECONDS = 24 * HOURS_IN_SECONDS;
const WEEKS_IN_SECONDS = 7 * DAYS_IN_SECONDS;
const YEARS_IN_SECONDS = 365 * DAYS_IN_SECONDS;

time(2 * YEARS_IN_SECONDS + 5 * DAYS_IN_SECONDS + 3 * HOURS_IN_SECONDS);

// En este caso sólo mostramos los años ya que no contamos con las semanas
// salida: "2y"

// Ejemplo 2
// 3 años (en segundos) + 1 semana (en segundos) + 3 días (en segundos) + 59 segundos

time(3 * YEARS_IN_SECONDS + WEEKS_IN_SECONDS + 3 * DAYS_IN_SECONDS + 59);

// En este caso se muestra hasta el número de días ya que no hay horas después de los días
// salida: "3y 1w 3d"
```

### Pre-requisitos

1. Realizar la práctica 3

### Pasos

1. Abrimos el proyecto de la práctica 3 y creamos un nuevo archivo dentro de nuestra carpeta `test`

```
touch test/time.test.js
```

2. Abrimos el archivo en algún editor y escribimos el siguiente código:

```js
const time = require("../src/time");

test("should return '0s' for 0 seconds", function () {
  // setup
  const seconds = 0;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("0s");
});
```

3. En una terminal ejecutamos el comando `npm test`

4. Nos mostrará un error ya que no contamos con el código de producción aun, por lo cual procederemos a crear el archivo correspondiente `src/time.js` con el siguiente contenido:

```js
function time(seconds) {
  // here is where you write your code...
}

module.exports = time;
```

5. Ejecutamos de nuevo el comando `npm test`, el cual ahora volverá a fallar por que la función no regresa el valor esperado:

```
npm test

> unit-test-kata@1.0.0 test
> jest

 FAIL  test/time.test.js
  ● should return '0s' for 0 seconds

    expect(received).toEqual(expected) // deep equality

    Expected: "0s"
    Received: undefined

       9 |
      10 |     // expectation
    > 11 |     expect(result).toEqual("0s");
         |                    ^
      12 |   });
      13 |
      14 |

      at Object.toEqual (test/time.test.js:11:20)
```

6. Agregamos el código mínimo para que la prueba pase:

```js
// src/time.js
function time(seconds) {
  return "0s";
}

module.exports = time;
```

7. Ejecutamos de nuevo las pruebas y ahora deberían pasar:

```
npm test

> unit-test-kata@1.0.0 test
> jest

 PASS  test/time.test.js
 PASS  test/hello.test.js

Test Suites: 2 passed, 2 total
Tests:       4 passed, 4 total
Snapshots:   0 total
Time:        0.159 s, estimated 1 s
Ran all test suites.
```

8. Hacemos un commit de nuestro código hasta este punto

```
git status
git add .
git commit -m "Se agrega función time y prueba unitaria para validar 0 segundos"
```

9. Ahora debemos nuevos escenarios, pero antes modificamos un poco nuestro script para correr las pruebas, para ello abrimos el archivo `package.json`

```
"scripts": {
    "test": "jest",
    "test:watch": "jest --watch"
},
```

9. En una nueva terminal corremos el comando `npm run test:watch`, para que se ejecute automáticamente cada vez que realicemos cambios.

10. Agregamos el escenario para 1 segundo

```js
// test/time.test.js

// other tests...

test("should return '1s' for 1 second", function () {
  // setup
  const seconds = 1;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("1s");
});
```

11. Observamos que la prueba falla, por lo cual procedemos a modificar nuestro código para que pase:

```js
// src/time.js
function time(seconds) {
  return seconds + "s";
}

module.exports = time;
```

12. Realizamos un nuevo commit:

```
git status
git add .
git commit -m "Se agrega escenario 1 segundo"
```

> **Nota**: Cada vez que nuestro código pase las pruebas debemos realizar un commit para asegurarnos de que tenemos un punto estable en todo momento.

13. Agregamos los escenarios para 2, 3 y 59 segundos. Podemos copiar las pruebas anteriores y cambiar los parámetros de entrada y el resultado esperado. Notamos que en este caso no es necesario modificar el código ya que las pruebas están pasando.

```js
// test/time.test.js

// other tests...

test("should return '2s' for 2 seconds", function () {
  // setup
  const seconds = 2;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("2s");
});

test("should return '3s' for 3 seconds", function () {
  // setup
  const seconds = 3;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("3s");
});

test("should return '59s' for 59 seconds", function () {
  // setup
  const seconds = 59;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("59s");
});
```

14. Agregamos una prueba para validar los minutos

```js
// test/time.test.js

// other tests...

test("should return '1m' for 60 seconds", function () {
  // setup
  const seconds = 60;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("1m");
});
```

15. La nueva prueba debe fallar, ya que no tenemos preparado el código para este nuevo escenario. Modificamos el código para que ahora pase las pruebas:

```js
// src/time.js
function time(seconds) {
  if (seconds === 60) {
    return "1m";
  }
  return seconds + "s";
}

module.exports = time;
```

16. Con esto ya debería pasar. Agregamos más pruebas

```js
// test/time.test.js

// other tests...

test("should return '2m' for 120 seconds", function () {
  // setup
  const seconds = 120;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("2m");
});
```

17. Modificamos el código para que pase de nuevo:

```js
// src/time.js
function time(seconds) {
  if (seconds >= 60) {
    const minutes = seconds / 60;
    return minutes + "m";
  }
  return seconds + "s";
}

module.exports = time;
```

18. De nuevo agregamos más escenarios para 3 y 59 minutos.

> Tip: para mejorar la legibilidad de las pruebas se pueden utilizar constantes para el número de minutos.

```js
// test/time.test.js

// other tests...

test("should return '3m' for 180 seconds", function () {
  // setup
  const seconds = 3 * 60;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("3m");
});

test("should return '59m' for 59 minutes", function () {
  // setup
  const seconds = 59 * 60;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("59m");
});
```

19. Procedemos a generar los escenarios para horas, días, semanas y años, siguiendo un razonamiento similar.

20. Agregamos los escenarios de unidades compuestas (Estas son sugerencias, pero se pueden agregar más escenarios)

```js
// test/time.test.js

// other tests...

test("should return '3m 20s' for 200 seconds", function () {
  // setup
  const seconds = 200;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("3m");
});

test("should return '1h 20m' for 80 minutes", function () {
  // setup
  const seconds = 80 * 60;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("1h 20m");
});

test("should return '2y 3w 4d 9h 45m 12s' for 755 days, 585 minutes and 12 seconds", function () {
  // setup
  const seconds = 755 * DAYS_IN_SECONDS + 585 * 60 + 12;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("2y 3w 4d 9h 45m 12s");
});
```

21. Realizamos los cambios en nuestro código de producción para que pasen los escenarios.

22. Agregamos los escenarios finales

```js
// test/time.test.js

// other tests...

test("should return '1h' for 1 hour and 9 seconds", function () {
  // setup
  const seconds = 3609;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("1h");
});

test("should return '2y 3w' for 751 days and 360 minutes", function () {
  // setup
  const seconds = 751 * DAYS_IN_SECONDS + 360 * 60;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("2y 3w");
});

test("should return '1w 2d' for 9 days, 35 seconds", function () {
  // setup
  const seconds = 9 * DAYS_IN_SECONDS + 35;

  // execute
  const result = time(seconds);

  // expectation
  expect(result).toEqual("1w 2d");
});
```

23. Agregar el código necesario para que pasen las pruebas

## Práctica 5: Publicar repositorio a Github

En esta práctica el alumno publicará su código en Github para la evaluación del código.

### Pre-requisitos

1. Contar con una cuenta en Github y estar agregado a la organización de la materia.
2. Realizar la práctica 4

### Pasos

1. Abrimos un navegador e ingresamos a la siguiente [dirección](https://github.com/orgs/EstandaresDeCalidadSW23/repositories).
2. Damos clic en el botón **New Repository**
3. En el nombre del repositorio tecleamos lo siguiente: `tu-nombre-unit-test-kata`. Ejemplo `benjamin-unit-test-kata`.
4. Seleccionamos la opción Public como tipo de repositorio
5. Dejamos las demás opciones sin modificar y damos clic en el botón **Create repository**
6. En la siguiente pantalla nos da la opción para publicar nuestro proyecto existente (Opción `"…or push an existing repository from the command line"`)

```
git remote add origin git@github.com:EstandaresDeCalidadSW23/benjamin-unit-test-kata.git
git branch -M main
git push -u origin main
```

7. Recargar la página y ver que los archivos se encuentran ya disponibles
