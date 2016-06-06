---
title: "Primeros pasos con Jekyll"
---

Hace tiempo que llevo teniendo ganas de hacer mi propio blog y había oído hablar sobre Jekyll pero nunca lo había usado. Me puse manos a la obra y aquí os cuento mis pasos e investigación sobre Jekyll:

##¿Que Es Jekyll?

Jekyll es una herramienta para crear blogs estáticos. Un blog sencillo que será rápido realizar y consultar. Y además se puede alojar en Github Pages de forma gratuita!! (Esto último me chifló)

##¿Como Instalar Jekyll?
Requerimientos:
- Tener ruby instalado.

Se puede instalar en Linux, Unix, ó Mac OS X. En mi caso tengo un Linux Debian.
Lo primero es crear una carpeta del proyecto en el directorio que queramos o bien, si queremos tener un repositorio en GitHub lo más fácil es crear allí el proyecto y clonarlo en la ruta deseada.

Entramos en el directorio elegido e instalamos Jekyll:

    sudo gem install jekyll

Una vez instalado, tecleamos el siguiente comando para asegurarnos de que jekyll está funcionando.

    jekyll -v

El comando debería mostrar la versión de Jekyll, justo de la siguiente manera:

![](https://s3.amazonaws.com/f.cl.ly/items/3U2h3P0S190V293B3g1F/Selecci%C3%B3n_005.png)

##Crear nuestro blog

Para crear un nuevo blog con Jekyll, debemos de teclear jekyll new y el nombre del sitio en la consola. De la siguiente manera:

    jekyll new blog

En este ejemplo, se crea un nuevo directorio de nombre blog:

Para arrancar el servidor de Jekyll basta con el comando:

    jekyll serve

Este comando tiene la opcion **--watch**, la cual hace que nuestro blog se actualice cada vez que hacemos un cambio en el código.
Para verlo funcionando abrimos el navegador y ponemos la url: “localhost/4000”

Ahora debemos abrir el navegador web y escribir **http://localhost:4000** y vualá! nos da la bienvenida:

![](https://s3.amazonaws.com/f.cl.ly/items/3J2f0x2g1W29031I2v0c/Selecci%C3%B3n_003.png)

Está es la configuración por defecto del index.html que trae Jekyll

##A tener en cuenta
Jekyll maneja una estructura de documento específico, el cual tenemos que seguir, para que el blog pueda funcionar correctamente.

![](https://s3.amazonaws.com/f.cl.ly/items/2G0i3U013s2p0P1x2t2Y/Selecci%C3%B3n_002.png)

###_config.yml;
Es el archivo de configuración del blog escrito en Yaml. En este archivo se puede especificar el nombre del blog, el formato de enlace permanente, host, número de puerto...

###_layouts
son las plantillas que usaremos. Para llamar a un layout deberemos incluir lo siguiente en la cabecera de nuestro HTML:

![](https://s3.amazonaws.com/f.cl.ly/items/0l3F3h0T2b2n2Z142w1s/Selecci%C3%B3n_004.png)


###_posts
Aqui escribiremos todos nuestros artículos, deben estar escritos en Markdown ó Textile. El nombre de estos ficheros siempre debe obedecer a una misma estructura: 2015-12-31-titulo-del-post.md (**año-mes-dia-titulo-del-post.md**).

###_site
Este es el directorio donde Jekyll compila todo una vez que arrancamos el servidor. Ya estaría listo para subirlo a nuestro servidor.

###_sass
Aqui incluimos nuestros archivos de estilo.

###_includes
Aquí irán nuestras porciones de código que se suelen repetir en nuestras páginas, los cuales vamos a ir añadiendo con includes en nuestros layouts.

##Escribimos el primer post
Creamos un fichero con la estructura anteriormente mencionada año-mes-dia-titulo.md y la guardamos en la carpeta _posts.
La manera de escribir el contenido ha de ser [markdown]( https://es.wikipedia.org/wiki/Markdown)

Lo primero tenemos que definir el título y la disposición del contenido. Se debe establecer dentro de la línea de triple de puntos. He aquí un ejemplo:

Entonces podemos escribir el contenido debajo de esta última línea.
Guardamos el archivo y al entrar de nuevo al navegador veremos el articulo creado.

***
***

Esto es una pincelada muy introductoria, por lo demás es ir investigando depende de lo que queramos para nuestro blog.
Resaltar que hay varios diseños ya realizados, de los cuáles yo cogí uno, los podéis encontrar [aqui](http://jekyllthemes.org/).
De esa forma los adaptáis a vuestro gusto teniendo ya la parte de diseño pre-fabricada :)
