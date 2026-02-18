<template>
    <div>
        <nuxt-layout name="layout-eight">

            <hero-banner-two />
            <!-- breadcrumb area start -->

            <h2 class="authorities-title wow fadeInUp" data-wow-delay=".5s">
            Conoce a nuestras autoridades
          </h2>


            <team-area-four />


            <!-- about area start -->
            <about-four spacing="pt-90 pb-90" />
            <!-- about area end -->

            <!-- about campus area start -->
            <!-- about campus area end -->

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University About - Acadia" });
</script>


<style scoped>

/* ===== Sección Autoridades ===== */
.authorities-section {
  position: relative;
}

/* Título con fondo institucional */
.authorities-title {
  position: relative;
  background: linear-gradient(135deg, #b1040e, #8f0a12);
  color: #ffffff;
  padding: 30px 40px;
  border-radius: 18px;
  font-size: 42px;
  font-weight: 800;
  text-align: center;
  letter-spacing: -0.5px;
  box-shadow: 0 18px 45px rgba(177, 4, 14, 0.28);
  overflow: hidden;
}

/* Efecto decorativo moderno */
.authorities-title::after {
  content: "";
  position: absolute;
  top: -50px;
  right: -50px;
  width: 180px;
  height: 180px;
  background: rgba(255, 255, 255, 0.08);
  border-radius: 50%;
}

/* Línea inferior elegante */
.authorities-title::before {
  content: "";
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 120px;
  height: 4px;
  background: #ffffff;
  border-radius: 4px;
  opacity: 0.7;
}

/* Responsive */
@media (max-width: 991px) {
  .authorities-title {
    font-size: 24px;
    padding: 22px;
  }
}

</style>