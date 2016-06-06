---
title: "Mejorando fichero routes.rb de Rails"
---
Mas que una entrada al blog, son unos apuntes personales que quiro tomar y plasmar aqui. Detalles que me han parecido interesantes si estamos definiendo nuestro fichero routes.rb

##WITH_OPTIONS

Muchas veces nos encontramos con este caso en nuestras rutas (fichero routes.rb):

    resources :students, only[:index]
    resources :teachers, only[:index]
    resources :classrooms, only[:index]

donde solo queremos acceder a una lista (acción index), sin acceder a las demás acciones.

Para que quede más estético nuestro código podemos traducirlo a esta otra forma:

    with_options only: :index do |list_only|
      list_only.resources :students
      list_only.resources :teachers
      list_only.resources :classrooms
    end

##CONSTRAINTS

Si por ejemplo trabajamos en una API y queremos añadir un subdominio a nuestras rutas, lo podemos especificar así:

    resources :students, constraints: { subdomain: ‘api’ }
    resources :teachers, constraints: { subdomain: ‘api’ }
    resources :classrooms, constraints: { subdomain: ‘api’ }

Pero mejor de esta otra manera:

    constraints subdomain: ‘api’ do
      resources :students
      resources :teachers
      resources :classrooms
    end

Y eso es todo :)
