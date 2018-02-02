# Function Scope - Java Script

## Asignacion

Leer el codigo javascript e identificar las funciones globales, locales, funciones de callback, expresions, statement, clousure, scope, contextos de ejecucion, que funciones forman parte de la pila de ejecucion (stack execution) y que funciones forman parte de la cola de eventos (event queue) Conceptos revisados el día de hoy. Para ello crearan un archivo markdown(.md) titulado function-scope-js

~~~js
$(document).ready(function() {
  
  console.log('Probar con el numero valido 4544164785372342');      
  
  // Declaramos las variables que vamos a utilizar
  var $inputCard = $('#card-number');
  var $inputMonth = $('.input-month');
  var $inputYear = $('.input-year');
  var $buttonNext = $('#next');
  var regexOnlyNumbers = /^[0-9]+$/;
  var labelErrorOrSuccessMessages = $('label[for="card-number"]');
    
  // Identificar el evento que nos permite capturar el input del usuario
  $inputCard.on('input', function() {
    isValidCreditCard($(this).val().trim());
  });
  
  // Funciones que habilita el boton del formulario
  function activeButton() {
    $buttonNext.attr('disabled', false);
  } 
 
  // Funcion que desabilita el boton del formulario
  function desactiveButton() {  
    $buttonNext.attr('disabled', true);
  } 

  // Funcion que valida la longitud del input ingresado por el usuario
  function longitud(input) {
    if (input.trim().length === 16) {
      return input;
    }
  }
  
  // Funcion que valida la longitud del input ingresado por el usuario
  function soloNumeros(input) {
    var regex = /^[0-9]+$/;
    if (regex.test(input)) {
      return input;
    }
  }
 
  // Funcion que valida que sea una un numero de tarjeta valido   
  function isValidCreditCard(numberCard) {
    var creditCardNumber = soloNumeros(longitud(numberCard));
    if (creditCardNumber !== undefined) {
      var arr = [];
      var sumaTotal = 0;
      for (var index = creditCardNumber.length - 1; index >= 0; index--) {
        arr.push(creditCardNumber[index]);
      }
      for (var index = 1; index < arr.length; index = index + 2) {
        arr[index] = arr[index] * 2;
        if (arr[index] >= 10) {
          arr[index] = arr[index] - 9;
        }    
      }
     
      for (var index = 0; index < arr.length; index++) {
        sumaTotal = sumaTotal + parseInt(arr[index]);
      }
     
      if (sumaTotal % 10 === 0) {
        console.log('Es una tarjeta valida');
        activeButton();
      } else {
        console.log('No es un numero valido');
        desactiveButton();
      }
    } else {
      console.log('Verifique el numero de su tarjeta'); 
      desactiveButton();  
    }
  }
});
~~~

### 1. Funciones Globales 

Son las funciones globales dentro del contexto de ejecucion de window. En el codigo se encuentra la siguiente funcion global:

~~~js
$(document).ready(function() {});
~~~

### 2. Variables Globales

Variables que pueden ser llamadas en cualquier momento dentro del contexto de ejecucion global. Dentro del codigo encontramos las siguientes variables globales

~~~js
  var $inputCard = $('#card-number');
  var $inputMonth = $('.input-month');
  var $inputYear = $('.input-year');
  var $buttonNext = $('#next');
  var regexOnlyNumbers = /^[0-9]+$/;
  var labelErrorOrSuccessMessages = $('label[for="card-number"]');
~~~

### 3. Funciones Locales

Funciones que estan definidas dentro de otras funciones. En el codigo se encuentra las siguientes funciones locales:

~~~js
function activeButton() {}
~~~
~~~js
function desactiveButton() {}
~~~
~~~js
function longitud() {}
~~~
~~~js
function soloNumeros() {}
~~~
~~~js
function isValidCreditCard() {}
~~~
~~~js
function isValidCreditCard() {}
~~~

### 4. Variables Locales

- Dentro de la function soloNumeros tenemos:
~~~js
var regex = /^[0-9]+$/;
~~~

- Dentro de la function isValidCreditCard tenemos:
~~~js
var creditCardNumber
~~~
~~~js
var arr = [];
var sumaTotal = 0;
~~~

### 5. Funciones Callback

Funciones que llaman a otras funciones, como parametro de estas. En el codigo se encuentra la siguiente funcion callback: 

~~~js
soloNumeros(longitud(numberCard))
~~~

### 6. Funciones Expresions

Funciones que son asignadas a variables. En el codigo se encuentra la siguiente:

~~~js
var creditCardNumber = onlyNumber(length(numberCard));
~~~

### 7. Funciones  Statement

6. Funciones Clousure

7. Funciones que forman parte de la fila de ejecucion (stack execution)

8. Funciones forman parte de la cola de eventos (event queue)


