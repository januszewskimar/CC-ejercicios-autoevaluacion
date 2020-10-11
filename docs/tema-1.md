# Tema 1 - Arquitecturas software para la nube

## Ejercicio 1
## Buscar una aplicación de ejemplo, preferiblemente propia, y deducir qué patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?

El sistema lo desarrollé en la asignatura Sistemas de Información basados en Web. Se trata de un sistema Web sobre eventos deportivos que permite tanto la consulta de datos por parte del usuario como la administración del sistema por parte de los administradores. La arquitectura es de tipo MVC (modelo, vista, controlador) y los lenguajes usados son PHP, HTML, CSS y JavaScript. El modelo se encarga de obtener y modificar la información. La información se almacena en una base de datos de tipo SQL. En ella existen tablas para los datos de los usuarios, grupos, permisos de grupos, los eventos y comentarios de eventos, etc. Existe una clase con métodos que realizan consultas y modificaciones en la base de datos. La vista se encarga de presentar los datos en un modelo adecuado para el usuario. Se utiliza PHP, HTML junto con el motor de plantillas Twig, CSS y JavaScript (este último por el lado del cliente). El controlador actúa de intermediario entre el modelo y la vista.

Para pasar a una arquitectura de microservicios, habría que dividir la aplicación en módulos pequeños de manera que puedan funcionar de forma independiente, en distintas máquinas. Además, sería necesario crear interfaces REST correspondientes para que los módulos puedan comunicarse entre sí. En cuanto al paso de los datos, dado que estos están estructurados, podrían enviarse en formato JSON.

## Ejercicio 2
## En la aplicación que se ha usado como ejemplo en el ejercicio anterior, ¿podría usar diferentes lenguajes? ¿Qué almacenes de datos serían los más convenientes?

La aplicación podría escribirse en otros lenguajes, como, por ejemplo, JavaScript usando Node. Sin embargo, si se optara por la arquitectura de microservicios, se tendría muchos más lenguajes para elegir. Considero el almacen de tipo SQL adecuado, ya que los datos están estructurados, referenciados entre sí en las distintas tablas.
