<template>
  <section>

    <div class="section">
      <div class="titulo">
        <div class="uni">
          <span class="destacada">L</span>a <span class="destacada">M</span>oraleja
        </div>
        <div class="modal" tabindex="-1" role="dialog" v-if="mostrarCarrito">
          <div v-if="showModal" class="modal">
            <div class="modal-content">
              <h1
                style="font-size: 30px; width: 100%; background-color: #1351e2dc;border: solid 1px black; margin: 0; border-radius: 35px;">
                Carrito de Compras</h1>
              <table>
                <thead>
                  <tr>
                    <th></th>
                    <th>Producto</th>
                    <th>Cantidad</th>
                    <th>Precio</th>
                    <th></th>
                  </tr>

                </thead>
                <tbody>
                  <tr v-for="(producto, index) in carrito" :key="index">
                    <td><img :src="producto.img" :alt="producto.nombre" class="imagen-producto"></td>
                    <td>{{ producto.text }}</td>
                    <td>{{ producto.cantidad }}</td>
                    <td>${{ producto.Libra.toLocaleString("es-ES", {
                      style: "currency",
                      currency: "COP",
                      minimumFractionDigits: 0,
                      maximumFractionDigits: 2,
                      useGrouping: true
                    }) }}
                    </td>
                    <td><button @click="agregarCarrito(index)"
                        style="background-color: transparent; border: 0; cursor: pointer; font-size: x-large;"
                        id="agregar">➕</button></td>
                    <td><button @click="eliminarCarrito(index)"
                        style="background-color: transparent; border: 0; cursor: pointer; font-size: x-large;"
                        id="menos">❌</button></td>
                    <td><button @click="borrarcarrito(index)"
                        style="background-color: transparent; border: 0; cursor: pointer; font-size: x-large;"
                        id="borrar">🗑️</button></td>
                  </tr>
                </tbody>
              </table>
              <div
                style="display: flex; flex-direction: row; justify-content: space-between; align-items: center;justify-content: center;">
                <span>Total:</span>
                <span style="align-items: end;">${{ calcularTotal().toLocaleString("es-ES", {
                  style: "currency",
                  currency: "COP",
                  minimumFractionDigits: 0,
                  maximumFractionDigits: 2,
                  useGrouping: true
                }) }}</span>
              </div>
                <button @click="limpiar(index)"
                style="background-color: rgb(18, 14, 63); border: 0; cursor: pointer; font-size: x-large; color: wheat;">LIMPIAR</button>
                <button @click="cerrar(index)"
                style="background-color: rgb(18, 14, 63); border: 0; cursor: pointer; font-size: x-large; color: wheat;">CERRAR</button>
            </div>
          </div>
        </div>
        <button class="carrito" style="background-color: transparent; border: solid 0px;"
          @click="mostrarCarrito = !mostrarCarrito"> 🛒</button>
      </div>
      <div class="superior">
        <div class="fondo-imagen"></div>
        <div class="contenedor">
          <div class="texto">Sea Bienvenido al Supermercado la Moraleja<br>
            <input type="text" placeholder="¿Que articulo desea?">
          </div>
        </div>
      </div>
    </div>
    <div class="Producto">
      <p> <strong>Seccion de Productos</strong></p>
    </div>
    <div class="articulo">
      <div class="descuento">
        <p style="font-size: 20px;"> <strong>EXCASOS</strong></p>
      </div>
      <div class=" cards">
        <div v-for="(item, index) in imagenes" :key="index" class="card" style="color: white;">
          <img :src="item.img" style="border-bottom: solid 2px grey;">
          <h1>{{ item.text }}</h1>
          <h2 style="font-size: 16px; color: black;">Libra a ${{ item.Libra }}
          </h2>
          <button class="color" @click="agregarAlCarrito(item)" style="margin-bottom: 20px"> ➕ </button>
        </div>
      </div>



      <div class="descuento">
        <p style="font-size: 20px;"> <strong>LOS MAS ADQUIRIDOS</strong></p>
      </div>
      <div class=" cards-dos">
        <div v-for="(item, index) in imagenes2" :key="index" class="card">
          <img :src="item.img" style="border-bottom: solid 2px grey;">
          <h1>{{ item.text }}</h1>
          <h2 style="font-size: 16px; color: black;">Libra a  ${{ item.Libra }}</h2>
          <button class="color" @click="agregarAlCarrito(item)" style="margin-bottom: 20px"> ➕ </button>
        </div>
      </div>
      <div class="descuento">
        <p style="font-size: 20px;"> <strong>MENOS SOLICITADOS</strong></p>

      </div>
      <div class=" cards-dos">
        <div v-for="(item, index) in imagenes3" :key="index" class="card">
          <img :src="item.img" style="border-bottom: solid 2px grey;">
          <h1>{{ item.text }}</h1>
          <h2 style="font-size: 16px; color: black;">Precio ${{ item.Libra }}</h2>
          <button class="color" @click="agregarAlCarrito(item)" style="margin-bottom: 20px"> ➕ </button>
        </div>
      </div>
    </div>

  </section>
</template>

<script setup>
import { ref } from 'vue';
import img1 from '/src/1.jpg';
import img2 from '/src/2.jpg';
import img3 from '/src/3.jpg';
import img4 from '/src/4.jpg';
import img5 from '/src/5.jpg';
import img6 from '/src/6.jpg';
import img7 from '/src/7.jpg';
import img8 from '/src/8.jpg';
import img9 from '/src/9.jpg';
import img10 from '/src/10.jpg';
import img11 from '/src/11.jpg';
import img12 from '/src/12.jpg';


const imagenes = ref([{

  img: img1, text: "Papa Criolla", Libra: 2704
}, {
  img: img2, text: "Cebolla Roja", Libra: 1000
}, {
  img: img3, text: "Cebolla Blanca", Libra: 1000
}, {
  img: img4, text: "Zanahoria", Libra: 1000
}])
const imagenes2 = ref([{
  img: img5, text: "Brocoli", Libra: 1000
}, {
  img: img6, text: "Tomate", Libra: 1000
}, {
  img: img7, text: "Calabazin", Libra: 1000
}, {
  img: img8, text: "Yuca", Libra: 1000
}])
const imagenes3 = ref([{
  img: img9, text: "Fresa", Libra: 1000
}, {
  img: img10, text: "Kiwi", Libra: 1000
}, {
  img: img11, text: "Naranja", Libra: 1000
}, {
  img: img12, text: "Piña", Libra: 1000
}])

const mostrarCarrito = ref(false);
function moneda(precio) {
  return precio.toLocaleString("es-ES", {
    style: "currency",
    currency: "COP",
    minimumFractionDigits: 0,
    maximumFractionDigits: 2,
    useGrouping: true
  })
}


const carrito = ref([])
const agregarCarrito = (index) => {
  carrito.value[index].cantidad++;
}
const borrarcarrito = (index) => {
  carrito.value.splice(index, 1);
}
const eliminarCarrito = (index) => {
  if (carrito.value[index].cantidad > 1) {
    carrito.value[index].cantidad--;
  } else {
    carrito.value.splice(index, 1);
  }
}
const showModal = ref(true);
const agregarAlCarrito = (item) => {
  let carritoItem = carrito.value.find(cartItem => cartItem.text === item.text);
  if (carritoItem) {
    carritoItem.cantidad++;
  } else {
    carritoItem = { ...item, cantidad: 1 };
    carrito.value.push(carritoItem);
  }
  showModal.value = true;
}
const calcularTotal = () => {
  let total = 0;
  for (const producto of carrito.value) {
    total += producto.Libra * producto.cantidad;
  }
  return total;
}
const cerrar = () => {
  mostrarCarrito.value = false;
}
function limpiar() {
  carrito.value = [];
}

</script>

<style scoped>
body {
  margin: 0%;

}

.card {
  border: solid 3px rgb(0, 0, 0);
  background-color: white;
  
}

.color {
  background-color: greenyellow;
  width: 30%;
  
}

.cards {
  display: flex;
  flex-wrap: wrap;
  justify-items: center;
  justify-content: space-around;
  align-items: center;
  text-align: center;
}

.cards-dos {
  display: flex;
  flex-wrap: wrap;
  height: 30%;
  justify-items: center;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 2%;
}

img {
  width: 220px;
  height: 200px;
}

.modal-body {
  display: flex;
  flex-direction: column;
  background-color: rgb(0, 0, 0);
}

.producto {
  display: flex;
  align-items: center;
  flex-direction: column-reverse;
}

.modal {
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 50;
}

.modal-content {
  display: flex;
    flex-direction: column;
    gap: 10px;
    width: 60%;
    max-height: 80%;
    background-color: rgb(19, 118, 210);
    color: white;
    text-align: center;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgb(0 0 0 / 50%);  
}

.imagen-producto {
  width: 80px;
  height: 80px;
  margin-right: 10px;
}

.detalles-producto {
  flex-grow: 1;
}

.titulo {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  text-align: center;
  font-size: 180%;
  align-items: center;
  background-color: rgb(54, 100, 158);
  height: 13%;
  align-content: center;
  color: rgb(255, 255, 255);
}

.contenedor {
  display: grid;
  grid-template-columns: 50% 50%;
  text-align: center;
  font-size: 150%;
  align-items: center;
  height: 100%;
}

.carrito {
  font-size: 100%;
}

.superior {
  align-content: center;
  height: 90%;
  width: 100%;
  position: relative;
}

.fondo-imagen {
  background-image: url(./fotico.jpg);
  filter: blur(5px);
  height: 98%;
  width: 100%;
  position: absolute;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

.section {
  background-color: black;
  height: 70vh;
}

.carrito-container {
  background-color: white;
  color: black;
}

.texto {
  color: white;
  position: relative;
  z-index: 1;
}

.Producto {
  display: flex;
  background-color: white;
  height: 20%;
  color: rgb(0, 0, 0);
  align-items: center;
  justify-content: center;
  border: solid 3px black;
  margin-top: 0.1%;
  font-size: 150%;

}

.articulo {
  background-image: url(./fondo.jpg);
  border: solid 2px black;
  height: 100%;
  text-align: center; 
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

.blanco {
  background-color: white;
  width: 100%;
  height: 1%;
}

.destacada {
  font-size: 180%;
  color: rgb(255, 255, 255);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.descuento {
  color: rgb(0, 0, 0);
  text-align: center;
}

.primer {
  color: red;
  font-size: 15px;
  padding-bottom: 10px;
}

h1 {
  color: black;
}
</style>