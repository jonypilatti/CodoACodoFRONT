<script setup>
import { ref } from 'vue'
import ArrowBack from '@/assets/icons/arrow_back.webp'
import ArrowForward from '@/assets/icons/arrow_forward.webp'
const tagNumber = ref(0)
const imagesArray = [
  'https://media2.westword.com/den/imager/u/original/18080251/20231018_195913.jpg',
  'https://casasincreibles.cl/wp-content/uploads/2018/10/llave-en-mano-mas-info.jpg',
  'https://media.revistaad.es/photos/60c74f971009e93ca111a794/master/w_1600%2Cc_limit/131405.jpg',
  'https://www.criterioonline.com/wp-content/uploads/2016/01/casa785-Copy.jpg'
]
const homeDescriptions = [
  {
    title: 'Casa Bonita',
    subtitle: 'En Alquiler',
    paragraph:
      'Bienvenido a la Casa Bonita, una joya arquitectónica que combina elegancia y comodidad. Esta propiedad de alquiler cautivará tus sentidos con sus amplios espacios abiertos, acabados de lujo y una distribución funcional. Disfruta de la tranquilidad de los jardines privados o relájate en la piscina de diseño mientras disfrutas de la brisa fresca. Ubicada en un exclusivo vecindario, esta casa te brindará un estilo de vida envidiable.'
  },
  {
    title: 'Lujosa Villa Costera',
    subtitle: 'En Alquiler',
    paragraph:
      'Descubre la increíble Lujosa Villa Costera, una propiedad de alquiler que te transportará al paraíso. Con una arquitectura vanguardista y una ubicación privilegiada frente al mar, esta villa te ofrecerá una experiencia de lujo incomparable. Disfruta de amplias terrazas con vistas panorámicas, una piscina infinita y acceso directo a una playa privada. Déjate mimar por los servicios de primera clase y vive unas vacaciones inolvidables en este oasis de tranquilidad y exclusividad.'
  },
  {
    title: 'Chalet de Montaña Acogedor',
    subtitle: 'En Alquiler',
    paragraph:
      'Experimenta la belleza natural y la serenidad en el Chalet de Montaña Acogedor. Esta propiedad de alquiler es el refugio perfecto para aquellos que buscan escapar del ajetreo de la vida cotidiana. Rodeado de impresionantes paisajes montañosos y bosques frondosos, este chalet te brindará un ambiente acogedor y acogedor. Disfruta de noches junto a la chimenea, caminatas por senderos impecables y actividades al aire libre sin fin. Una experiencia única que te dejará renovado y lleno de energía.'
  },
  {
    title: 'Residencia Urbana Vanguardista',
    subtitle: 'En Alquiler',
    paragraph:
      'Prepárate para vivir en el corazón de la ciudad con la Residencia Urbana Vanguardista. Esta propiedad de alquiler está diseñada para aquellos que buscan un estilo de vida moderno y sofisticado. Con su arquitectura de vanguardia y su diseño interior minimalista, esta residencia te ofrecerá un ambiente fresco y contemporáneo. Disfruta de la comodidad de estar cerca de los mejores restaurantes, tiendas y centros de entretenimiento, todo a tu alcance.'
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
