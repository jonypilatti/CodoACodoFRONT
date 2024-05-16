<script setup>
import { ref } from 'vue'
import ArrowBack from '@/assets/icons/arrow_back.webp'
import ArrowForward from '@/assets/icons/arrow_forward.webp'
const tagNumber = ref(0)
const imagesArray = [
  'https://media2.westword.com/den/imager/u/original/18080251/20231018_195913.jpg',
  'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQspH9CgayNr3mJ-Cmm5z0trD8JCFoEX0ebeDHgCiCdcA&s',
  'https://casasincreibles.cl/wp-content/uploads/2018/10/llave-en-mano-mas-info.jpg',
  'https://media.revistaad.es/photos/60c74f971009e93ca111a794/master/w_1600%2Cc_limit/131405.jpg'
]
const homeDescriptions = [
  {
    title: 'Mansión de Lujo en la Costa',
    subtitle: 'En Venta',
    paragraph:
      'Prepárate para disfrutar de la vida de ensueño en la Mansión de Lujo en la Costa. Esta impresionante propiedad en venta te ofrecerá una experiencia de lujo sin igual. Con su arquitectura de diseño y sus acabados de primera calidad, esta mansión es un verdadero monumento a la sofisticación. Disfruta de amplias salas de estar, una cocina gourmet de ensueño y un impresionante jardín con piscina y spa. Además, su ubicación privilegiada frente al mar te brindará vistas panorámicas impresionantes.'
  }
]

const AddNumber = () => {
  if (tagNumber.value < imagesArray.length - 1) {
    tagNumber.value += 1
  }
}
const LessNumber = () => {
  if (tagNumber.value > 0) {
    tagNumber.value -= 1
  }
}
</script>

<template>
  <div class="wrapperA">
    <button @click="LessNumber" class="prev">
      <img :src="ArrowBack" alt="Previous" />
    </button>
    <div class="wrapperB">
      <div class="imgContainer">
        <img :src="imagesArray[tagNumber]" alt="ImagenCarrusel" class="img" />
      </div>
      <article class="article">
        <h3 class="title">{{ homeDescriptions[tagNumber].title }}</h3>
        <p class="subtitle">{{ homeDescriptions[tagNumber].subtitle }}</p>
        <p class="paragraphs">{{ homeDescriptions[tagNumber].paragraph }}</p>
      </article>
    </div>
    <button @click="AddNumber" class="next">
      <img fill="red" :src="ArrowForward" alt="Next" />
    </button>
  </div>
</template>

<style scoped>
.wrapperA {
  display: flex;
  flex-direction: row;
  width: 100%;
  min-height: 80vh;
  position: relative;
  padding: 15px;
  padding-left: 0;
}
.wrapperB {
  display: flex;
  flex-direction: row;
  align-self: center;
}
.img {
  width: 100%;
  height: 100%;
}
.prev {
  position: absolute;
  height: 50px;
  width: 50px;
  left: -60px;
  border-radius: 12px;
  top: calc(50% - 50px);
}
.prev:hover {
  background-color: #6d2c31;
  transform: scale(1.1);
}

.prev:focus {
  outline: none;
}
.imgContainer {
  width: 100%;
  height: 60%;
}
.next {
  position: absolute;
  height: 50px;
  width: 50px;
  border-radius: 12px;
  right: -60px;
  top: calc(50% - 50px);
}
.next:hover {
  background-color: #6d2c31;
  transform: scale(1.1);
}

.next:focus {
  outline: none;
}
.list-item {
  display: flex;
  flex-direction: row;
  padding: 15px;
  color: red;
}
.article {
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 70%;
  padding-left: 15px;
  padding-right: 15px;
  margin-right: 50px;
}
.title {
  font-size: 40px;
}
.subtitle {
  font-size: 32px;
}
.paragraphs {
  font-size: 24px;
}
@media (max-width: 768px) {
  .wrapperA {
    flex-direction: column;
  }
  .wrapperB {
    flex-direction: column;
    align-items: center;
  }
  .title {
    font-size: 24px;
  }
  .subtitle {
    font-size: 20px;
  }
  .paragraphs {
    font-size: 16px;
  }
  .article {
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 75%;
    padding-left: 15px;
    padding-right: 15px;
    margin-right: 0px;
  }
  .prev {
    position: absolute;
    height: 50px;
    width: 50px;
    left: 0px;
    border-radius: 12px;
    top: calc(70%);
  }
  .next {
    position: absolute;
    height: 50px;
    width: 50px;
    border-radius: 12px;
    right: 0px;
    top: calc(70%);
  }
}
.prev img,
.next img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
</style>
