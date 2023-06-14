# Callbacks-en-javascript
En este repositorio intentare explicar lo mas simple posible que son los callbacks y en que situaciones es utilizado.

# Que son los callbacks?

Una función de devolución de llamada o callbacks es una función que se pasa a otra función como argumento, que luego se invoca dentro de la función externa para completar algún tipo de rutina o acción. 

Primeramente tenemos que un callbacks es una funcion, por lo tanto creemos un funcion:
  
    function miCallback(){
      console.log('Operacion Completada');
    }

Luego dicha funcion debemos pasar a otra funcion como argumento, recordemos que los argumentos son valores que se pasan a un funcion cuando se le invoca:
    
    let nombre = 'Pedro'
    miFuncion(nombre); // Aqui lo que hicimos fue pasarle la varialbe nombre que es igual a 'Pedro' como argumento al invocar a nuestra         funcion.


Por lo tanto, nos dice que la funcion de devolucion de llamada puede ser pasada como argumento, por lo que nuestro codigo quedaria de la siguiente manera.

        function miCallback(){
            console.log('Operacion Completada');
        };
        
        miFuncion(miCallback); // Aqui lo que hacemos es pasarle nuestra funcion 'miCallback', como argumento al invocar la funcion 'miFuncion', 
        
Nos quedaria crear la funcion 'miFuncion', en el cual especificaremos el parametro que recibira como argumento al ser invocado. Para refrescar la memoria, los parametros de las funciones son variables locales que se utilizan para almacenar los argumentos que se le pasa a la funcion al ser invocado.

    function miFuncion(callback){
        // Aqui realizaremos alguna accion
        
        // Luego llamamos al callback
        callbck(); // 
      
    };

    function miCallback(){
      console.log('Accion completada');
    };
    
    miFuncion(miCallback);

Cualquier función que se pasa como argumento a otra función para que pueda ejecutarse en esa otra función se llama como función de devolución de llamada.

# En que situacion utilizar la funcion de devolucion de llamada y cuales son sus beneficios?

Las devoluciones de llamada se utilizan para manejar los resultados de las operaciones asincrónicas, lo que significa que la operación no bloquea la ejecución del resto del programa. En cambio, el programa continúa ejecutándose y la función de devolución de llamada se ejecuta cuando se completa la operación. Aqui es fundamental comprender en que consisten las operaciones asincronas, como asi tambien las sincronas, para ello nos detendremos un momento y centremonos por un instante en estos dos tipos de operaciones.

`#` Operaciones sincronas

  Comenzaremos con las operaciones sincronas, en que consisten? Las operaciones síncronas son aquellas que se ejecutan de forma secuencial, una tras otra, en el orden en que se encuentran en el código. Durante la ejecución de una operación síncrona, el programa se bloquea y no puede continuar con la ejecución de otras tareas hasta que la operación actual haya finalizado.
  
  Ejemplo:
      
        function operacionBloqueante() {
        // Simulación de una operación bloqueante que toma 5 segundos
        const startTime = new Date().getTime();
        while (new Date().getTime() < startTime + 5000) {
          // Realiza tareas durante 5 segundos
        }
        console.log("Operación bloqueante completa");
        }

        console.log("Inicio del programa");
        operacionBloqueante();
        console.log("Fin del programa");
        
        
Si ejecutamos este codigo, veremos el siguiente resultado en la consola:

      Inicio del programa
      Operación bloqueante completa
      Fin del programa

Primeramente se ejecuta el primer console.log imprimiendo 'Inicio de progama', luego se invoca a la funcion 'operacionBloqueante()', el cual contiene un bucle que realiza tareas durante 5 segundos, durante esos 5 segundos no se ejecuta el codigo siguiente, a esto lo llamamos operacion bloquente, ya no no permite la realizacion de otra tarea, posterioremnte se ejecuta el el console.log imprimiendo 'Operacion bloquente completada', y finalmente se imprime 'Fin de programa', por lo tanto podemos comprobar que la ejecucion fue secuencial una tras otra.


`#` Operaciones asincronas

Una operación asíncrona no bloquea la ejecución del programa y permite que otras tareas se realicen mientras espera que la operación se complete.

Veamos un ejemplo:

    function f1() {
    console.log('f1');
    }

    function f2() {
        console.log('f2');
    }

    function main() {
        console.log('main');
        setTimeout(f1, 0);
        f2();
    }

    main();
    
    
En este ejemplo tenemos tres funciones f1(), f2() y main(), y la secuencia de ejecucion es la siguiente:

  1 - Primeramente se invoca la funcion main()
  2 - Dentro del mismo, en primer lugar tiene un console.log('f2'), imprimiendo 'f2'.
  3 - Posteriormente se llama a la funcion setTimeout(), el cual contiene una funcion de devolucion de llamada.
  4 - La funcion f1, no se ejecuta inmediatamente, por mas que le indicamos que el tiempo de ejecucion de la funcion sea en 0 segundos.
  5 - Por lo tanto, vemos que se ejecuta la funcion f2(), el cual contiene un console.log('f2'), imprimiendo 'f2'
  6 - Inmediatemente luego se ejecuta la funcion f1, el cual contiene un console.log('f1'), imprimiendo 'f1'
  

Es importante tener en cuenta que, aunque setTimeout con un retardo de 0 milisegundos puede parecer asincrónico, sigue siendo un truco para programar una ejecución retrasada y no garantiza un comportamiento realmente asincrónico. En situaciones reales, las operaciones asincrónicas involucran interacciones con recursos externos, como solicitudes de red o lectura/escritura de archivos, que pueden llevar tiempo y no se pueden lograr simplemente utilizando setTimeout.

Ahora bien, veamos un caso real de una operacion asincronica:

    function obtenerNombre(callback) {
      // Realiza una solicitud a la API utilizando fetch
     fetch(URL)
        .then((response) => response.json()) // Convierte la respuesta en formato JSON
        .then((response) => {
          // Filtra las palabras de la respuesta que tienen una longitud de 5 caracteres
          diccionario = response.filter((palabra) => palabra.length == 5);

          // Obtiene una palabra aleatoria del diccionario y la convierte a mayúsculas
          palabra = diccionario[Math.floor(Math.random() * diccionario.length)].toUpperCase();

          // Llama a la función de devolución de llamada con la palabra obtenida
          callback(palabra);
        })
        .catch((err) => {
          // Maneja cualquier error que ocurra durante la solicitud
          console.log("Ha ocurrido un error");
        });
    }

    function imprimirPalabra(palabra) {
      // Imprime la palabra en la consola
      console.log(palabra);
    }

    // Llama a la función obtenerNombre pasando imprimirPalabra como callback
    obtenerNombre(imprimirPalabra);

    

La función imprimirPalabra es el callback que se pasa a obtenerNombre. Recibe la palabra como argumento y en este caso, simplemente la imprime en la consola.

Al llamar a obtenerNombre y pasar imprimirPalabra como callback, se ejecutará la secuencia de operaciones asincrónicas: realizar la solicitud a la API, filtrar y seleccionar una palabra, y finalmente llamar a imprimirPalabra con la palabra obtenida.

  


      




