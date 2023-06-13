# callbacks-en-javascript
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



      




