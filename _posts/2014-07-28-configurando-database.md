---
title: "Configurando database.yml con Mysql"
---

Un ejemplo básico de este fichero para nuestro proyecto es el siguiente: 

{% highlight ruby %}
default: &default
  adapter: mysql2
  encoding: utf8
  pool: 5
  username: root
  password:
  host: localhost
{% endhighlight %}
development:
  <<: *default
  database: nombre_proyecto_development

test:
  <<: *default
  database: nombre_proyecto_test

production:
  <<: *default
  database: nombre_proyecto_production
  username: nombre_proyecto
  password: <%= ENV['NOMBRE_PROYECTO_DATABASE_PASSWORD'] %>

Este fichero tiene información sensible, son las contraseñas para acceder a nuestros diferentes servidores de Mysql en los entornos configurados. 

Normalmente este fichero ha de estar en el repositorio remoto sin mostrar ninguna contraseña. 

Para ello, realizamos lo siguiente:

Para el entorno de desarrollo:

En el momento de hacernos un git clone del proyecto, tendremos nuestro database.yml tal y como se muestra, pero eso nos resultaría inútil si no ponemos nuestra contraseña del mysql local en caso de que dispongamos de ella.  Lo que quedaría de la siguiente forma:


default: &default
  adapter: mysql2
  encoding: utf8
  pool: 5
  username: root
  password: 1234
  host: localhost

En el momento que tengamos que hacer un git status para ver los cambios realizados, nos indicará que vamos a subir cambios del fichero “database.yml”, lo que nosotros no queremos hacer, (no queremos hacer pública nuestra contraseña!). La solución a esto es indicar a Git que ese fichero lo ignore aunque haya cambios en el.

Dos maneras de hacer esto:
Una es ir al fichero que se encuentra dentro de la carpeta de nuestro proyecto: .git/info/exclude y añadir la siguiente línea: 

config/database.yml

Con ello se ignorarán los cambios realizados en este fichero y al hacer un git status no se mostrará, cuando hagamos un git push de nuestro código al repositorio, estos cambios no se enviarán.

La segunda manera es hacerlo en el fichero .gitignore_global, todo lo que pongamos en este fichero afectará a todos los proyectos que tengamos, esto es importante tenerlo en cuenta.
$ git config --global core.excludesfile ~/.gitignore_global

rtante


https://help.github.com/articles/ignoring-files/

 



En el lugar de trabajo usábamos una práctica que a mi no me terminaba de convencer, poner el fichero “database.yml” en el .gitignore. 
Con ello, compartíamos un fichero “database.example” en el repositorio común sin contraseñas y cada uno en su local, teníamos un “database.yml” (copia de database.example) pero con nuestras propias contraseñas de nuestro entorno development.

El otro día aprendí a guardar las contraseñas en una variable de entorno de nuestro sistema unix. Voy a mostrar como hacerlo:

Disponer de un fichero “database.yml” en nuestra aplicación, y donde queramos usar las contraseña poner lo siguiente: ENV[‘MI_PASSWORD’]
