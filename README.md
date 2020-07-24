# Sails
Projects with Sails



---
sails --help
---

npm install sails
sails new --help
// usar el proyecto fast sin carpetas opciones ( -- no front-end o  --fast )
sails new webapp --fast 
cd webapp
yarn install
yarn add sails-postgresql --save

// configurar estado de migrate:safe, en config/models para datos creados no se crean nuevos
//configurar api/config/datastores   (se configura fuenre de datos ) adaptador y url

adapter: require('sails-postgresql'),
    url: 'postgresql://postgres:123@localhost:5432/test',


// correr la aplicación  puerto 1337
sails lift 

// se crea el modelo ( la forma manual consiste en crear un archivo en  models,

sails generate model Vendedor nombre:string desde:number email

// configurar controller en api/controller
--------
  fn: async function (inputs, exits) {

    const vendedores = await Vendedor.find()
    return exits.success({vendedores: vendedores});

  }
--------
 fn: async function (inputs, exits) {
    const articulos = await Articulo.find().populate('usuario').populate('comentarios')
    return exits.success({articulos: articulos});
  }


// generar modelos con atributos

sails generate model Vendedor nombre:string desde:number

// se cofigura pages en views/pages si crea stilos en assests/pages.ejs/controllers/styles/js 

sails generate page contacto


----
<h1>Contacto</h1>
<p>
  <ul>
    <% vendedores.forEach( vendedor => { %>
    <li><%=vendedor.nombre%> (Desde: <%=vendedor.desde%>)</li>
    <% }) %>
  </ul>
</p>
-----
<h1>Inicio</h1>

<p>Articulos disponibles</p>

<table>
  <thead>
    <tr>
      <th>Marca</th>
      <th>Modelo</th>
      <th>Descripción</th>
      <th>Precio</th>
      <th>Usuario</th>
      <th>Comentarios</th>
    </tr>
  </thead>
  <tbody>
    <% articulos.forEach(articulo=> { %>
      <tr>
        <td><%=articulo.marca%></td>
        <td><%=articulo.modelo%></td>
        <td><%=articulo.descripcion%></td>
        <td><%=articulo.precio%></td>
        <td><%=articulo.usuario.nombre%></td>
        <td>
          <ul>
            <% articulo.comentarios.forEach( comentario => { %>
              <li><%=comentario.descripcion%></li>
            <% }) %>
          </ul>
        </td>
      </tr>
    <% }) %>
  </tbody>
</table>
-----
// 


// generar un nuevo action para modifica bases de datos

sails generate action crear 

//Necesitas ubicar los archivos action del GET config/routes.js

---
  '/terminos-y-condiciones': { view: 'pages/terminos_y_condiciones' },
  '/crear': { action: 'crear' },
---

// despues configurar y verificar la ruta en api/controllers/models


/////////VISTAS

cambiar el layout, colocar la img

//.tmp/public/images




// Sesion 

 sails generate controller sesion


FINNNNN
-----


EXTRA
---


	Validación
custom	una función personalizada que realiza la validación
isAfter	valida si es después de una fecha dada
isBefore	valida si es antes de una fecha dada
isBoolean	si es true (verdadero)  o false (falso)
isCreditCard	si es un número de tarjeta de crédito
isIP	si es un IP
isNumber	si es número
isURL	si es URL
max	máximo para un número
min	mínimo para un número
maxLength	máximo número de caracteres
minLength	mínimo número de caracteres
regex	si cumple una expresión regular

Esperamos que estas funciones sean de utilidad en tus futuros desarrollos.
PSTRGESSQL

//añadir funcionalidades
yarn add nodemon --save
npx nodemon app.js
yarn add sails-hook-flash
--


insert into vendedor values ('1','2015,'Dave')

insert into articulo values (1,'Negro','Dave','renault',1,17000000)	



---

///////////Lifecycle Callbacks!
// Las funciones callback de ciclo de vida de los modelos permiten ejecutar un código dado un evento.
// Existen 6 funciones las cuales se listan a continuación:

NombreEvento	Parámetros
beforeCreate	Antes de crear
afterCreate	Después de crear	
beforeUpdate	Antes de actualizar
afterUpdate	Después de actualizar	
beforeDestroy	Antes de eliminar
afterDestroy	Después de eliminar	

----
///////Idiomas

// va a la carpeta /config/i18n.js/ configurar idiomas  con locales

// puede colocar idioma por defecto con defaultLocale: 'es'

// debe configurar carpeta de idiomas en config/locales/en.json 

{"palabra":"Traduccion}

//usar el identificador de la palabra con ._ en el ejs de la vista 

<%=sails._("palabra")%> | <%=sails._("palabra" %s>

--//middlewares///

//uso de mensajes para la consola o ´procesamiento de funciones config/log.js
//uso de middlewares, config/http.js 

sails.log.debug(variable)





<


