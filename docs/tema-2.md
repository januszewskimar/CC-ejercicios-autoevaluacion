# Tema 2 - Desarrollo basado en pruebas

## Ejercicio 1. Instalar alguno de los entornos virtuales de node.js (o de cualquier otro lenguaje con el que se esté familiarizado) y, con ellos, instalar la última versión existente, la versión minor más actual de la 4.x y lo mismo para la 0.11 o alguna impar (de desarrollo).

He optado por *nvm* y para instalarlo he descargado un script de [este repositorio](https://github.com/nvm-sh/nvm).

![Captura de la instalación de nvm](/docs/imgs/tema-2/instalacion-nvm.png?raw=true)

Una vez ejecutado el script, ha sido necesario ejecutar el siguiente comando que recarga el fichero *~/.bashrc*

```
source ~/.bashrc
```

A partir de este momento se puede ejecutar *nvm*. Para ver las versiones disponibles se ejecuta:

```
nvm list-remote
```

Las últimas entradas se ven en la siguiente imagen:

![List-remote - últimas entradas](/docs/imgs/tema-2/nvm-list-remote.png?raw=true)

Para instalar la versión más reciente, se ejecuta:

```
nvm install node
```

![Captura de la instalación de la versión más reciente de Node](/docs/imgs/tema-2/nvm-instalar-mas-actual.png?raw=true)

Para instalar otra versión, se ejecuta:

```
nvm install versión
```

En la salida de *list-remote* miré las versiones 4.x:

![List-remote de 4.x](/docs/imgs/tema-2/nvm-versiones-4.png?raw=true)

Después ejecuté el comando correspondiente:

![Captura de la instalación de la versión 4.9.1](/docs/imgs/tema-2/nvm-install-4.png?raw=true)

Para instalar la versión 0.11, miré las siguientes entradas:

![List-remote de 0.11](/docs/imgs/tema-2/nvm-versiones-0.11.png?raw=true)

E instalé la versión correspondiente:

![Captura de la instalación de la versión 0.11.16](/docs/imgs/tema-2/nvm-install-0.11.png?raw=true)


## Ejercicio 2. Crear una descripción del módulo usando package.json. En caso de que se trate de otro lenguaje, usar el método correspondiente.

He creado un [repositorio](https://github.com/januszewskimar/example) en *GitHub* para la aplicación de prueba y posteriormente he realizado un *clone* en una carpeta local. Después he ejecutado el siguiente comando:

```
npm init
```

Al ejecutar este comando, aparecen preguntas para cada paso como se puede ver en la imagen de abajo.

![Resultados de npm init](/docs/imgs/tema-2/npm-init.png?raw=true)

## Ejercicio 3 Descargar el repositorio de ejemplo anterior, instalar las herramientas necesarias (principalmente Scala y sbt) y ejecutar el ejemplo desde sbt. Alternativamente, buscar otros marcos para REST en Scala tales como Finatra o Scalatra y probar los ejemplos que se incluyan en el repositorio.

Primero realicé un *clone* del repositorio con el comando que viene a continuación:

```
git clone https://github.com/JJ/spray-test
```

En [esta página](https://www.scala-lang.org/download/) encontré información sobre cómo instalar *Scala*. Primero es necesario instalar Java. Opté por la versión 8 del JDK y lo instalé con el comando:

```
sudo apt install openjdk-8-jdk
```

En la página había un [enlace](https://www.scala-sbt.org/download.html) al proceso a seguir en el caso de sbt. En la imagen de abajo se pueden ver los comandos ejecutados:

![Instalación de sbt](/docs/imgs/tema-2/sbt-instalacion.png?raw=true)

Después ejecuté *sbt* en la carpeta del repositorio con el comando que viene a continuación:

```
sbt
```

El resultado se puede ver en la siguiente imagen:

![Ejecución de sbt](/docs/imgs/tema-2/sbt-ejecucion.png?raw=true)

Ejecuté los comandos y pruebas que venían en el *README* del repositorio. El primero fue test, que compila todo y ejecuta los test.

![Ejecución de tests en sbt](/docs/imgs/tema-2/sbt-test.png?raw=true)

El siguiente ha sido *re-start*, que lanza la aplicación. El resultado está reflejado en la siguiente imagen.

![Ejecución de re-start en sbt](/docs/imgs/tema-2/sbt-re-start.png?raw=true)

Una vez lanzada la aplicación, abrí el navegador para ver qué devolvía en la dirección correspondiente:

![Test de Spray en el navegador](/docs/imgs/tema-2/spray-test-navegador.png?raw=true)

Realicé otras pruebas con *curl*:

![Test de Spray con curl](/docs/imgs/tema-2/spray-tests-curl.png?raw=true)

Con *re-stop* apagué la aplicación.

![Ejecución de re-stop en sbt](/docs/imgs/tema-2/sbt-re-stop.png?raw=true)

## Ejercicio 4. Para la aplicación que se está haciendo, escribir una serie de aserciones y probar que efectivamente no fallan. Añadir tests para una nueva funcionalidad, probar que falla y escribir el código para que no lo haga. A continuación, ejecutarlos desde mocha (u otro módulo de test de alto nivel), usando descripciones del test y del grupo de test de forma correcta. Si hasta ahora no has subido el código que has venido realizando a GitHub, es el momento de hacerlo, porque lo vamos a necesitar un poco más adelante.

El repositorio se creó durante la realización del ejercicio 2. He creado un archivo de una clase llamada Str que almacena una cadena de caracteres y tiene tres métodos:
* *getCapitalized()* que devuelve la cadena almacenada con los caracteres en mayúscula
* *getLowerCased()* que devuelve la cadena almacenada con los carácteres en minúscula
* *getReversed()* que debería devolver la cadena almacenada invertida. No estaba implementada al principio. Devolvía la cadena almacenada sin ningún cambio

Creé un archivo de pruebas con dos ejemplos que testeaban cada función. Comenté las aserciones correspondientes a la función *getReversed()*. El fichero se puede ver en la imagen que viene abajo:

![Archivo de pruebas](/docs/imgs/tema-2/test-asserts.png?raw=true)

Modifiqué el archivo *package.json* para que ejecutara el archivo antes mencionado:

![package.json con test básicos usando assert](/docs/imgs/tema-2/package-json-asserts.png?raw=true)

El resultado se ve en la siguiente imagen:

![Tests en npm - 1](/docs/imgs/tema-2/npm-tests-1.png?raw=true)

Después descomenté las líneas correspondientes a *getReversed()*, por lo cual, al ejecutar el test, surgió un error que se ve en la imagen que viene a continuación:

![Tests en npm - 2](/docs/imgs/tema-2/npm-tests-2.png?raw=true)

Después implementé la función *getReversed()* y preparé el test para *Mocha*. Cambié la configuración en *package.json* para que ejecutara *Mocha*:

![package.json con test en Mocha](/docs/imgs/tema-2/package-json-mocha.png?raw=true)

Después ejecuté el comando correspondiente que se ve en la captura de pantalla que viene a continuación:

![Tests en npm - 3](/docs/imgs/tema-2/npm-tests-3.png?raw=true)

Todos los test han tenido éxito.


# Ejercicio 5. Haced los dos primeros pasos antes de pasar al tercero.

Me registré en *Travis*. Seleccioné el repositorio correspondiente a la aplicación:

![Selección de respositorio en Travis](/docs/imgs/tema-2/travis-repos.png?raw=true)

Posteriormente subí un archivo de configuración y entré de nuevo en *Travis*. La prueba se ejecutó con éxito y el resultado se ve en la imagen que viene a continuación:

![Travis - éxito](/docs/imgs/tema-2/travis-exito.png?raw=true)
