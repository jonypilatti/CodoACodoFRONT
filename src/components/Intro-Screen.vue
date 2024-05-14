<script setup>
import { ref } from 'vue'
const tagNumber = ref(0)
const imagesArray = [
  'https://media2.westword.com/den/imager/u/original/18080251/20231018_195913.jpg',
  'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQspH9CgayNr3mJ-Cmm5z0trD8JCFoEX0ebeDHgCiCdcA&s',
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
    title: 'Resort Spa Ultra Fit',
    subtitle: 'Para vacacionar',
    paragraph:
      'Prepárate para sumergirte en un oasis de relajación y bienestar en el Resort Spa Ultra Fit. Nuestras instalaciones de vanguardia, como el spa de clase mundial, el centro de fitness de última generación y los campos de golf impecables, te brindarán una experiencia de vacaciones incomparable. Disfruta de servicios personalizados, desde masajes relajantes hasta clases de yoga al aire libre, mientras te mimas en un entorno paradisíaco.'
  },
  {
    title: 'Casa Mansion Epica',
    subtitle: 'En venta',
    paragraph:
      'Prepárate para vivir una vida de lujo sin precedentes en la Casa Mansión Épica. Esta impresionante propiedad en venta es un verdadero monumento a la sofisticación y el buen gusto. Desde los detalles arquitectónicos impecables hasta los acabados de primera calidad, cada rincón de esta mansión ha sido cuidadosamente diseñado para satisfacer tus deseos más exigentes. Disfruta de amplias salas de estar, una cocina gourmet de ensueño y un impresionante jardín con piscina y spa.'
  },
  {
    title: 'Casa de juegos paradisiaca',
    subtitle: 'Para vacacionar',
    paragraph:
      '¿Estás listo para unas vacaciones llenas de emoción y diversión? La Casa de Juegos Paradisíaca es el destino perfecto para toda la familia. Esta propiedad única cuenta con un parque acuático privado, campos de minigolf temáticos, pistas de carreras de go-karts y mucho más. Disfruta de una experiencia de vacaciones completamente nueva, donde la diversión no tiene límites. Déjate sorprender por los increíbles detalles y la emoción interminable que te esperan.'
  },
  {
    title: 'Casa de los teletubbies',
    subtitle: 'Para jugar',
    paragraph:
      'Bienvenidos al mágico mundo de los Teletubbies, donde la imaginación no tiene límites. Esta propiedad única ha sido diseñada especialmente para los más pequeños, convirtiéndose en un verdadero parque temático en casa. Déjalos explorar la Casa de los Teletubbies, con sus coloridos rincones, piscinas de pelotas, toboganes y mucho más. Un entorno seguro y lleno de diversión que cautivará a tus pequeños y les brindará momentos inolvidables.'
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
    <button @click="LessNumber" class="prev">Prev</button>
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
    <button @click="AddNumber" class="next">Next</button>
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
.imgContainer {
  width: 100%;
  height: 60%;
}
.next {
  position: absolute;
  height: 50px;
  width: 50px;
  border-radius: 12px;
  right: -50px;
  top: calc(50% - 50px);
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
</style>
