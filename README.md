# Ejercicio de Vue - Task

[Platzi](https://platzi.com) ha colocado un ejercicio con el siguiente enunciado:

## Manipulación del DOM con Vue.js

Este ejercicio consiste en practicar la funcionalidad de renderizado declarativo que provee Vue.js, para eso vamos a crear una pequeña aplicación web que nos permita hacer seguimiento de tareas utilizando el local storage del Browser. Así vamos a reforzar los conceptos básicos que nos ofrece Vue.js para manipular e interactuar con el DOM.

***Ejercicio:***

* Crear dentro de data una propiedad “name” de tipo String y una propiedad “tasks” de tipo de Array.

* Agregar una expresión para mostrar el valor de name y utilizar la directiva apropiada para para mostrar en una lista cada uno de los elementos dentro de task. Cada “task” es un objeto con una propiedad “title” y otra “time”. Agreguemos las expresiones necesarias para que en cada tarea podamos visualizar ambas propiedades.

* Agregar funcionalidad para crear una nueva tarea:
    * Vamos a necesitar una nueva propiedad llamada “newTask” que sea un Object. Dentro de este objeto también agregamos una propiedad “tilte” de tipo String y una propiedad “time” de tipo Number. Recuerda inicializar las propiedades con valores default.

   * Vamos a crear un método llamado “addTask” que agregue una nueva tarea al array “tasks”. Una vez agregada también va a reiniciar los valores dentro de “newTaks”. Ten en cuenta que antes de agregar la propiedad debemos chequear con los valores de “newTask.title” y “newTask.time” existan (sean distintos de “falsy”). Por otro lado es importante que cada elemento nuevo que agreguemos al array de “tasks” sea un objeto nuevo y no la instancia de “newTask”.

   * Vamos a agregar el HTML, para esto necesitamos dos “inputs” y un “button”. También debemos agregar las directivas correspondientes para enlazar el código con la vista.

   * Creamos también una funcionalidad para cancelar, para eso debemos crear un método llamado “cancel” que simplemente reinicie los valores de las propiedades de newTask. Recordemos agregar un button de HTML donde enlazar este nuevo método.

   * Es momento de saber cuantas horas llevamos trabajadas, para eso vamos a crear una computed property llamada “totalTime” donde se recorran todas las tareas y se calculo el total del tiempo trabajado. También vamos agregar un elemento HTML con la expresión necesaria para visualizar la propiedad.

   * Debemos integrar la app con el local storage del browser. Dentro del metodo “addTask”, guardamos toda la lista de tareas en dicho storage usando este metodo: “localStorage.setItem(‘tasks’, JSON.stringify(this.tasks))”.

   * Guardando las tareas en el browser podemos persistir la información aunque estemos cerrando o refrescando la página. Además, al momento de crearse el componente, debemos leer esta información para poder cargar la lista de tareas. Para eso dentro del hook “created”, escribimos el siguiente código: “this.tasks = JSON.parse(localStorage.getItem(‘tasks’)) || []”

   * Lo último que nos queda es poder eliminar las tareas que ya no queremos. Para eso vamos a crear un método que se llame “removeTask”. Este método debe recibir por parámetro el indice de la tarea y podemos utilizar ese indice (en conjunto con el método “splice” de Array) para eliminar el elemento. Recordemos que tendremos que agregar un botón por cada tarea y cada uno de estos se encarga de llamar al método “removeTask” enviando por parámetro el indice correspondiente. Recordemos invocar la funcionalidad que ya pusimos en “addTask”, para actualizar el local storage del Browser.

   * Por último vamos a mejorar la UI, cuando no haya tareas podemos mostrar un mensaje que indica que no hay ninguna tarea cargada y por otro lado ocultar el lista vacía.

---

## Como instalar este ejercicio

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

---

## Demo
