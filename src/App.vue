<template>
  <section>
    <div class="section">
      <div class="titulo">
        <div class="uni">
          <span class="destacada">L</span>a <span class="destacada">M</span>oraleja
        </div>
        <div class="gestion"> 🛒</div>
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
        <p> <strong>Productos al 30% de descuento</strong></p>
        <p class="primer">(Solo aplicable por del 15 de Agosto al 15 de Septiembre)</p>
      </div>
      <div class=" cards">
        <div v-for="(item, index) in imagenes" :key="index" class="card" style="color: white;">
          <h1 class="text">{{ item.text }}</h1>
          <img :src="item.img" alt="">
          <h2>${{item.precio }}</h2>

        </div>
      </div>
      <div class="descuento">
        <p> <strong>Productos al 50% de descuento</strong></p>
        <p class="primer">(Solo aplicable del 15 de Septiembre al 01 de Diciembre)</p>
      </div>
      <div class=" cards-dos">
        <div v-for="(item, index) in imagenes2" :key="index" class="card">
          <img :src="item.img" alt="">
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
const imagenes = ref([{
  img: '/src/1.jpg', text: "Papa Criolla", precio: 1000
}, {
  img: '/src/2.jpg',
}, {
  img: '/src/3.jpg'
}, {
  img: '/src/4.jpg',
}])
const imagenes2 = ref([{
  img: '/src/5.jpg',
}, {
  img: '/src/6.jpg',
}, {
  img: '/src/7.jpg'
}, {
  img: '/src/8.jpg',
}])

function moneda(precio){
 return precio.toLocaleString("es-ES", {
              style: "currency",
              currency: "COP",
              minimumFractionDigits: 0,
              maximumFractionDigits: 2,
              useGrouping: true
            })
}



</script>

<style scoped>
body {
  margin: 0%;
  background-color: black;

}

.card {
  border: solid 3px rgb(255, 255, 255);

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
  height: 220px;
}

.titulo {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;

  text-align: center;
  font-size: 180%;
  align-items: center;
  background-color: rgb(54, 100, 158);
  height: 10%;
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

.gestion {
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
  opacity: 0.3;
  height: 100%;
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
  border: solid 2px black;
  height: 100%;
  background-color: rgb(32, 31, 31);
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
  color: rgb(255, 255, 255);
  text-align: center;
}

.primer {
  color: red;
  font-size: 15px;
  padding-bottom: 10px;
}</style>


