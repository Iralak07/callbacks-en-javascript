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
        
Nos quedaria crear la funcion 'miFuncion', en el cual especificaremos el parametro que recibira como argumento al ser invocado. Para refrescar la memoria, los parametros de las funciones son variables locales que se utiliza para almacenar los argumentos que se le pasa a la funcion al ser invocado.

    function miFuncion(callback){
      
    }

Una devolución de llamada de JavaScript es una función que debe ejecutarse después de que otra función haya terminado de ejecutarse. 

Cualquier función que se pasa como argumento a otra función para que pueda ejecutarse en esa otra función se llama como función de devolución de llamada. 
