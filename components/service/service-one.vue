<template>
    <section class="service-area tp-service-bg" style="background-image: url(/images/bg/services-bg.jpg);">
        <div class="container">
            <div class="row">

                <div v-for="(item) in service_data" class="col-lg-3 col-md-6">
                    <div class="tp-service-item text-center mb-40 wow fadeInUp" data-wow-delay=".3s">
                        <div class="tp-service-wrap">
                            <div class="tp-service-icon">
                                <span>
                                    <img :src="item.icon" alt="service-icon">
                                </span>
                            </div>
                            <h4 class="tp-service-title">
                                <nuxt-link href="/university-about">
                                    <div v-html="item.title"></div>
                                </nuxt-link>
                            </h4>
                            <div class="tp-service-btn">
                                <nuxt-link href="/university-about"><span><svg-arrow-right-two /></span></nuxt-link>
                            </div>
                        </div>
                        <div class="tp-service-content">
                            <p>{{ item.text }}</p>
                        </div>
                    </div>
                </div>

            </div>
            <div class="row">
                <div class="col-lg-12">
                    <div class="tp-service-all text-center">
                        <span>Con la confianza de 
                            <nuxt-link href="https://www.pucp.edu.pe/">PUCP
                                <svg-arrow-right-sm-two />
                            </nuxt-link>
                        </span>
                    </div>
                </div>
            </div>
        </div>
        <div class="tp-service-shape">
            <div class="tp-service-shape-1 wow bounceIn" data-wow-duration="1.5s" data-wow-delay=".4s">
                <img src="/images/shape/service/services-shape-1.png" alt="service-shape">
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">

const service_data = [
    {
        id: 1,
        icon: '/images/icon/service/service-icon-1.svg',
        title: "¿Por qué estudiar <br/> en el IESTP Ayaviri?",
        text: "Técnicos listos para trabajar en Puno y más allá. Laboratorios reales y profesores con experiencia.",
    },
    {
        id: 2,
        icon: '/images/icon/service/service-icon-2.svg',
        title: "Nuestro <br/> licenciamiento",
        text: "Título oficial del MINEDU + certificados por competencias. Reconocido en todo el Perú.",
    },
    {
        id: 3,
        icon: '/images/icon/service/service-icon-3.svg',
        title: "Nuestros <br/> Graduados",
        text: "Más de 500 egresados trabajando en mineras, empresas y emprendiendo en la región.",
    },
    {
        id: 4,
        icon: '/images/icon/service/service-icon-4.svg',
        title: "Plana <br/> Docente",
        text: "Profesores calificados y con experiencia laboral real. Siempre dispuestos a guiarte.",
    },
];
</script>
