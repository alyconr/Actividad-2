# Actividad-2
Los objetivos de esta sesión son adquirir conocimientos avanzados del lenguaje de  programación y explorar las diferencias entre JavaScript y Typescript.


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
    Asociar un Evento Click a un Elemento button con addEventListener
    

