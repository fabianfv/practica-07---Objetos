# Práctica 07 - Ejemplos de Objetos

Abre la consola para ver la salida

Ejemplo Persona

```javascript
const persona = {
  nombre: "Joan Manuel",
  edad: 74,
  ciudad: "Barcelona",
  dni: "4556777J",

  //Ineficiente: se crea una función toString para cada instancia
  toString: function toString() {
    return `Hola, soy ${this.nombre} con DNI: ${this.dni}, tengo ${this.edad} años y vivo en ${this.ciudad}`
  }, //la coma en la última propiedad o método la añade la extensión prettier cuando se usa el patrón literal
}

console.log("--------------------------------------------------")
console.log('Salidas del ejemplo "Persona"\n\n')

console.log("Presentarse: " + persona)
console.log("\n\n--------------------------------------------------\n\n")
```

Ejemplo Perros

```javascript
function Perro(nombre, ladrido, edad) {
  this.nombre = nombre
  this.ladrido = ladrido
  this.edad = edad
  this.decir_nombre = function decir_nombre() {
    return this.nombre
  }
  this.ladrar = function ladrar() {
    return this.ladrido
  }
  this.decir_edad = function decir_edad() {
    return (this.ladrido + " ").repeat(this.edad)
  }
}

const perro1 = new Perro("Goofy", "Wof!", 4, 3)
const perro2 = new Perro("Lassie", "Wooof!", 4, 4)
const perro3 = new Perro("Dido", "Auuuuuu!", 4, 5)
const perro4 = new Perro("Scooby-Doo", "Daba daba doooo!", 4, 6)
const perro5 = new Perro("Pluto", "Wof wof!", 4, 7)
const perro6 = new Perro("Firulais", "¡Guau!", 4, 8)

console.log('Salidas del ejemplo "Perro"\n\n')

for (perro of [perro1, perro2, perro3, perro4, perro5, perro6]) {
  console.log("Di tu nombre: ", perro.decir_nombre())
  console.log("Di tu edad: ", perro.decir_edad())
}

console.log("\n\n--------------------------------------------------\n\n")
```

Ejemplo Cotorra

```javascript
var Ciudad = function (nombre = "Palma", distancia_al_origen = 0) {
  this.nombre = nombre
  this.distancia_al_origen = distancia_al_origen
  this.obtener_nombre = () => this.nombre
  this.obtener_distancia_al_origen = () => this.distancia_al_origen
}

var Cotorra = function (energia = 1000, ciudad = palma) {
  this.energia = energia
  this.ciudad = ciudad

  this.obtener_energia = () => this.energia

  this.obtener_ciudad = () => this.ciudad

  this.cantar = () => "pri pri pri"

  this.comer_lombriz = () => (this.energia += 20)

  this.volar_en_circulos = () => (this.energia -= 10)

  this.distancia_a = (destino) =>
    Math.abs(destino.obtener_distancia_al_origen() - this.ciudad.obtener_distancia_al_origen())

  this.calcular_energia_gastada = (destino) => (this.energia -= this.distancia_a(destino) / 2)

  this.volar_hacia = function (destino) {
    this.calcular_energia_gastada(destino)
    this.ciudad = destino
  }
}

var palma = new Ciudad()
var manacor = new Ciudad("Manacor", 30)

console.log('Salidas del ejemplo "Cotorra"\n\n')

console.log("objeto palma, di tu nombre: ", palma.obtener_nombre())
console.log("objeto palma, dime tu distancia al origen: ", palma.obtener_distancia_al_origen())

console.log("objeto manacor, di tu nombre: ", manacor.obtener_nombre())
console.log("objeto manacor, dime tu distancia al origen: ", manacor.obtener_distancia_al_origen())

var pepita = new Cotorra()

console.log("-- A ver como canta pepitaaaaa: ", pepita.cantar())

console.log("-- Pepita, ¿dónde naciste?: ", pepita.obtener_ciudad().obtener_nombre())

console.log("-- Pepita, ¿qué tanta fuerza tienes?: ", pepita.obtener_energia())

pepita.comer_lombriz()
console.log(
  "-- ¡Muy bien Pepita! Hay que alimentarse bien, mira que tan grande y fuerte estás, dime cuánta energía tienes: ",
  pepita.obtener_energia()
)

console.log("Pepita, sale a dar una vuelta (en el horario permitido, por supuesto).")
pepita.volar_en_circulos()
console.log("-- ¡Cuánto ejercicio hiciste Pepita!, debes tener hambre, , dime cuánta energía tienes: ", pepita.obtener_energia())

console.log("-- Pepita, ve a visitar a la tía Cata.")
pepita.volar_hacia(manacor)
console.log("-- Pepita, ¡has vuelto! Qué cansada debes estar, dime cuánta energía tienes: ", pepita.obtener_energia())
```
