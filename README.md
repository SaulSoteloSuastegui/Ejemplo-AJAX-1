# Ejemplo-AJAX-1
###### Este código pertenece al siguiente videotutorial del canal de Youtube "Programación y más" [video](https://www.youtube.com/watch?v=Qk2cqRtWkDo&t=76s)

###### Consideraciónes para que el ejemplo funcione:

* Para que este código funcione, debe estar en un servidor apache, yo lo estoy probando en MAMP
* En la misma ubicación del archivo html tiene que estar el archivo.txt con algun diálogo.


###### ahora sin mas, les comparto mi código, con comentarios explicando cada paso.



```javascript
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Ajax - Ejercicio 2 - Ale DC</title>


    <script>
        // declaro la variable Global donde voy a instanciar el XMLHttpPequest.
        var peticionHTTP;


        // esta funcion inicializa el objeto XMLHttpRequest en la variable llamada "PeticionHTTP", declarada globalmente antes de esta función.

        function inicializar_XMLHttpRequest() {
            if (window.XMLHttpRequest)
                peticionHTTP = new XMLHttpRequest();
            else peticionHTTP = new ActiveXObject("Microsoft.XMLHTTP");
        }



        // esta funcion necesita 3 parametros: la URL, el METODO, y la Funcion de Respuesta
        function realizarPeticion(url, metodo, funcion) {

            //aca verifico el cámbio de estado y si está ok se procede con alguna funcion.
            peticionHTTP.onreadystatechange = funcion;

            // aca abro la peticion a la api, pasandole coƒmo mínimo, la URL y el Método HTTP, que siempre va a ser true de "Asyhnchronous".
            peticionHTTP.open(metodo, url, true);

            //esto no lo explicó aún.
            peticionHTTP.send(null);
        }


        //hace una llamada a la funcion realizarPeticion(url,método,funcion)
        function descargarArchivo() {
            inicializar_XMLHttpRequest();
            realizarPeticion('archivo.txt', 'GET', funcActuadora);
        }



        function funcActuadora() {

            alert('Actuando FuncActuadora');

            //verifico el estado de la peticion, tiene que ser 4.  [1 = CargaNdo] , [2 = Cargado!] , [3 = Interactivo] , [4 = Copmpleto]
            if (peticionHTTP.readyState == 4)

                // verifica el código del status HTTP, tiene que dar 200. [200 = OK] , [300 = Redirección] , [400 = Not Found] , [500 = Error Servidor]
                if (peticionHTTP.status == 200)

                    // si los dos if anteriores son verdaderos recién ahora ejecuta la sentencia de abajo.
                    document.write(peticionHTTP.responseText);
        }


        //invoca a la funcion y le pasa los valores
        //realizarPeticion('archivo.txt', 'GET', funcActuadora);

        window.onload = descargarArchivo;
    </script>



</head>

<body>

</body>

</html>
```

###### Saludos desde Rosario, Argentina.

###### Ale DC


