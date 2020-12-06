<template>
  <header>
    <nav class="navbar navbar-expand-lg sticky-top navbar-dark bg-dark">
      <a class="navbar-brand" href="#">
        <img
          src="../assets/grupo22.jpg"
          width="40 "
          height="30"
          class="d-inline-block align-top"
          alt=" "
          loading="lazy "
        />
        Sprint 2 Grupo 22
      </a>
      <div class="collapse navbar-collapse justify-content-end" id="navbarNav ">
        <ul class="nav nav-tabs">
          <li class="nav-item">
            <a class="nav-link" href="#"
              >Inicio <span class="sr-only">(current)</span></a
            >
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#services">Servicios</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#clima">Clima</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#team">Miembros</a>
          </li>
        </ul>
      </div>
    </nav>

    <!-- carousel -->
    <div id="carouselBanner" class="carousel slide" data-ride="carousel">
      <ol class="carousel-indicators">
        <li data-target="#carouselBanner" data-slide-to="0" class="active"></li>
        <li data-target="#carouselBanner" data-slide-to="1" class=""></li>
        <li data-target="#carouselBanner" data-slide-to="2" class=""></li>
        <li data-target="#carouselBanner" data-slide-to="3" class=""></li>
      </ol>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <img
            src="../assets/banner.jpg"
            class="d-block w-100"
            alt="Imagen Banner"
          />
          <div class="carousel-caption d-none d-md-block">
            <h4>
              <kbd class="text-primary"
                >Encuetra lo que buscas en nuestra Tienda Virtual</kbd
              >
            </h4>
          </div>
        </div>
        <div class="carousel-item">
          <img
            src="../assets/banner.jpg"
            class="d-block w-100"
            alt="Imagen Banner"
          />
          <div class="carousel-caption d-none d-md-block">
            <h5>
              <kbd class="text-primary"
                >Te ofrecemos una variedad de servicios. Desde apuestas, hasta
                compras online.</kbd
              >
            </h5>
          </div>
        </div>
        <div class="carousel-item">
          <img
            src="../assets/banner.jpg"
            class="d-block w-100"
            alt="Imagen Banner"
          />
          <div class="carousel-caption d-none d-md-block">
            <h5>
              <kbd class="text-primary"
                >Actualizate con lo último del clima y busca las condiciones ambientales 
                de la ciudad de tu interés</kbd
              >
            </h5>
          </div>
        </div>
        <div class="carousel-item">
          <img
            src="../assets/banner.jpg"
            class="d-block w-100"
            alt="Imagen Banner"
          />
          <div class="carousel-caption d-none d-md-block">
            <h5>
              <kbd class="text-primary"
                >Nuestro equipos de trabajo siempre está dispuesto a
                ayudarte.</kbd
              >
            </h5>
          </div>
        </div>
      </div>
      <a
        class="carousel-control-prev"
        href="#carouselBanner"
        role="button"
        data-slide="prev"
      >
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Anterior</span>
      </a>
      <a
        class="carousel-control-next"
        href="#carouselBanner"
        role="button"
        data-slide="next"
      >
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Siguiente</span>
      </a>
    </div>
    <!-- Fin carousel -->
  </header>
</template>

<script>
export default {
  name: "EncabezadoBanner",
};
</script>

<style scoped>
</style>