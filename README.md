# Actividad-2
Los objetivos de esta sesión son adquirir conocimientos avanzados del lenguaje de  programación y explorar las diferencias entre JavaScript y Typescript.
[Solución Ejercicios Ver Repo](https://github.com/alyconr/Javascript-Course/blob/alydev/activity/2_session/index.js)

## Ejercicio 1

Escribe un programa que tome como entrada un objeto y devuelva una lista con sus propiedades. Solo puede tener como entrada un objeto y el tipo de vuelta tiene que  ser un array.

```bash
var person = {
    name: 'Lucas',
    age: '27',
    profession: 'Developer'
};

const properties = Object.keys(person);
console.log(properties);

```
Output: // [ 'name', 'age', 'profession' ]

## Ejercicio 2 

Enumera los distintos valores que puede tener “this” y pon un ejemplo de cada uno.

## Contexto Global

```bash
console.log(this === window)  // true
```
Cuando se hace uso de this fuera de cualquie función siempre se hace referencia al objeto global. En el caso del navegador  hacemos referencia al objeto [window](window).

## En una función con modo estricto
 Las funciones que hacen uso del modo "strict" devuelven el valor "undefined" 
 ```bash
 function f1() {
     return this;
 }   
 f1(); // undefined
 ```
 
 ## En un metodo
```bash 
const person = { //propietario
    name: 'Aly',
    sayHello: function () { 
        return `Hola, soy ${this.name}` 
    }
}
person.sayHello(); // Hola, soy Aly
```
Dentro de un método this hae referencia al propietario.

## En una método con array funtion . 

```bash
const person = { 
    name: 'Aly',
    sayHello: () => { 
        console.log( `Hola, soy ${this.name}`)
    }
}

person.sayHello(); 
```

## En un Evento

```bash

function actionButtonReceiver(button) {
    console.log("Button pressed with->");
    console.log(button);
}
```

## Ejercicio 3 

Escribe una arrow function (ES6 function) que tome como parámetro una cadena y la  devuelva invertida. Ej "Hola mundo" quedaría "odnum aloH"

```bash
const cadenaInvertida = cadena => [...cadena].reverse().join('');
cadenaInvertida('hola mundo'); // odnum aloH
```

## Ejercicio 4

Crea una clase con el formato ES6. Esta clase va a tener dos atributos, “username” y “password” y un método login() que compruebe que username tiene el valor “admin” y password el valor “passwd” y en caso positivo, lance una alerta diciendo que el  usuario esté logeado, en caso contrario, que diga que el usuario o la contraseña son  incorrectas. Siendo que:
let login = new Login(“admin”, “passwd”) // alert -> User logged in
let logbad = new Login(“pepe”, “bad”) // alert -> User or passwd incorrect

```bash
class Login {
    constructor(username, password) {
        this.username = username;
        this.password = password;
    }

    logint ()  {
        let username;
        let password;
        if ( this.username === "admin" && this.password === "passwd" ) { 
            alert( "Usuario esta logueado");
        }
        else { 
            alert("Usuario o password incorrecto");
        }

    }
}
    let login = new Login("admin","passwd");
    let logbad= new Login("pepe","bad");

    login.logint(); // Usuario está logueado
    logbad.logint(); // Uusuario o password incorrecto
```

## Ejercicio 5 
   
   
En este ejercicio os voy a hacer mirar un poco de documentación extra. Y vamos a utilizar el fichero que se encuentra en activity/2_session/index.html.
Crea dos clickListener, para los botones con id loginSuccess y loginFailure. En el primero crearemos un objeto login que sea correcto y llamaremos a la función para que de el resultado correcto. En el segundo crearemos un objeto login con parámetros incorrectos y llamaremos a login para que falle. 
Para ello consulta los siguientes documentos.

```bash
document.getElementById("loginSuccess").addEventListener("click",logins,false);
function logins (){
  alert("correcto");
}

function cli () {
  let usernames;
  let passwords;
      if ( this.usernames === "admin" && this.passwords === "passwd" ) { 
          alert( "Usuario esta logueado");
      }
      else { 
          alert("Usuario o password incorrecto");
      }
 // alert("incorrecto");
}
let login1 = new cli("admin ","passwd");
document.getElementById("loginFailure").addEventListener("click",cli,false);
```

## Ejercicio 6

En este ejercicio vamos a añadir asincronía al resto de botones:
• Crea dos clickListener, para los botones con id loginSuccessAsync y loginFailureAsync. En el primero llamaremos a la función loginWithUsername
para que de el resultado correcto. En el segundo llamaremos a la función con parámetros incorrectos. Os dejo un par de pistas para resolver el ejercicio.
• Primero, addEventListener(‘click’, () => {}) no acepta asincronía ya que es una función síncrona. Pero es posible sustituir el segundo argumento () => {}, que es una función, por una función asíncrona (habría que añadir una palabra reservada que hemos visto).
• loginWithUsername devuelve una promesa, que lanza una excepción si falla, por lo que habría que atrapar esa excepción para que nuestro programa no 
falle

```bash
document.getElementById("loginSuccessAsync").addEventListener("click",loginWitUsername,false);
let loginWitUsername = async (username, password) => {
    return new Promise(function (resolve, rejected) {
      setTimeout(() => {
        if (username === "admin" && password === "passwd") {
          resolve("User logged in");
        } else {
          rejected("Error: invalid username or password");
        }
      }, 200);
    });
};
```
    

