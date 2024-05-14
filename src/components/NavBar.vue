<template>
  <nav class="navbar">
    <img
      src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQJ5-ys9Q_AWJwean5ovhpAYMRS50Ka72fT4F9URtVGIeg85cwxrZ2d71Xs4qkxJjTNgXk&usqp=CAU"
      alt="Logo"
      width="200px"
      height="80px"
      class="logo-img"
    />
    <ul class="list">
      <li type="" class="list-item">
        <a href="#inicio_id"> Inicio </a>
      </li>
      <li class="list-item">
        <a href="#venta_id"> Venta </a>
      </li>
      <li class="list-item">
        <a href="#alquiler_id"> Alquiler </a>
      </li>
      <li class="list-item">
        <a href="#publicar_id"> Publicar </a>
      </li>
      <li class="list-item">
        <a href="#contacto_id"> Contacto </a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.navbar {
  display: flex;
  width: calc(100vw - (100vw - 100%));

  padding-left: 15%;
  align-items: center;
  align-self: flex-start;
  position: relative;
  height: 100px;
  box-shadow: 5px 5px 5px 1px rgba(137, 55, 61, 0.8);
  background-color: #fad9a6;
}
.list {
  display: flex;
  width: 100%;
  padding-right: 15%;
  justify-content: space-between;
  align-items: center;
  list-style-type: none;

  flex-direction: row;
}
.list-item {
  color: #142433;
  font-size: 24px;
  font-family: Inter;
  &:hover {
    color: #89373d;
  }
}
.logo-img {
  border-radius: 12px;
  margin-right: 5%;
}
</style>
