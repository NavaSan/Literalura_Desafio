# Literalura Desafio Java

En  este desafio realizamos la peticion de una API de libros, en donde por medio de una peticion recogemos un JSON y en base de los datos que mas se nos hacen necesarios los guardamos en una base de datos en PostgresSQL, dentro de este desafio 
podemos observar las siguientes metas u objetivos a alcanzar:

  * Conectar y consumir una API.
  * Crear Modelos de datos para poder mapear nuestra respuesta de el archivo JSON.
  * Crear Repositorios para las consultas de cada tabla que crearemos.
  * Hacer la logica de guardar todo en nuestra base de datos.

como primer punto nos conectamos a la API utlizando el HttpClient de Java el cual nos permite crear una conexion HTTP, despues pasmos el cliente a un HttpRequest el cual ya nos permte por medio de la url entrar a los datos proporcionados,
y con HttpResponce podemos extraer toda la informacion. como un punto adicional tembien se creo un archivo par ala convercion de la respuesta a un JSON para manejar mejor la informacion.

Para crear los modelos extraje la informacion que queria guardar en mi base de datos con las anotaciones de @Entity y @Table pude crear esto en la base de datos, para pasar de un modelo de datos a los datos reales se debe de pasar por un filtro
el cual fue realizado en los archivos de Datos, donde extrajimos todo lo que estaba en la propiedad "result" del JSON que extrajimos esto lo pudimos hacer gracias a la anotacion @JsonAlias y para no tener problemas por lo demas campos del JSON
puse al inicio de la clase una anotacion la cual es @JsonIgnoreProperties(ignoreUnknown = true) esta propeidad ignora todo lo demas que no sea lo que pusimos en nuestro @JsonAlias, para esto hay que tener cudado con los nombres de los campos de 
nuestro JSON, las demas clases DatosLibro y DatosAutor siguen la misma logica.

En los repositorios se realizan los Querys que necesitamos llamar en nuestra clase principal, dentro de los cuales llamaremos dependiento lo que se valla a realizar, por ejemplo para realizar el SELECT de toda la tabla de autores o de libros 
solo se utlilizo la funcion integrada findAll la cual nos trae todos los registros que estamos seleccioando de un modelo en especifico.

Toda la logica realizada esta en la clase Principal de mi proyecot la cual esta dividia en la creacion de los menus y las funciones de cada uno de ellos, para correr de manera correcta el sistema hay que hacerlo directamente desde el archivo
LiteraluraDesafioApplication la cual es la que contiene los metodos necearios opara correr dicha aplicacion, para que pudiera ser una aplicacion de linea de comandos se necesito de implementar una clase la cual es CommandLineRunner esta nos crea
un metodo llamdo Run el cual lanza nuestra aplicacion en nuestra consola.
