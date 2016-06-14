---
title: "Usando Carrierwave con peticiones AJAX"
---

Carrierwave funciona estupendamente si lo implementamos en formularios rails:

    <%= form.file_field :avatars, multiple: true %>

o bien adjuntamos por consola:

    u = User.new
    u.avatar = params[:file] # Assign a file like this, or

    # like this
    File.open('somewhere') do |f|
      u.avatar = f
    end

    u.save!
    u.avatar.url # => '/url/to/file.png'
    u.avatar.current_path # => 'path/to/file.png'
    u.avatar_identifier # => 'file.png'

(ejemplos de la documentación oficial de la gema)

El problema que  yo me he encontrado es cuando lo quiero implementar a través de una petición AJAX, subiendo un archivo en un input de tipo ‘file’.

La manera que he tenido para que funcione es la siguiente:

Creamos un input en nuestra vista:
    <input id='miInput' type='file'/>

Y a través de nuestro código accedemos de la siguiente manera:

    var formData = new FormData();
    formData.append('user[avatar]', $(‘#miInput’)[0].files[0]);

    $.ajax({
      url: ‘url que corresponda’,
      data: formData,
      cache: false,
      contentType: false,
      processData: false,
      type: 'PUT'
    });

La cadena que escribimos ‘user[avatar]’ es lo que nuestro controlador rails espera que nos llegue en nuestros parámetros de la petición.

Ponemos contentType a false para forzar a JQuery que no añada un Content-Type por nosotros. Tambien processData a false para que JQuery no convierta nuestro formData en una cadena, pues nos dará error.

Esto se enviará al controlador de rails y vualá! Ya tenemos archivos adjuntos con peticiones AJAX funcionando perfectamente. :)
