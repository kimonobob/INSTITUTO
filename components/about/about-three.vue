<template>
    <section class="tp-about-year-area tp-about-year-bg p-relative pt-200 pb-95">
        <div class="tp-about-year-shape">
            <div class="shape-1">
                <img src="/images/our-mission/star.png" alt="">
            </div>
            <div class="shape-2">
                <img src="/images/our-mission/thumb-2-shape.jpg" alt="">
            </div>
        </div>
<h2 class="egresados-simple text-center">Nuestros Egresados</h2>

        <div class="tp-about-year-plr tp-about-year-nav">
            <Carousel v-bind="thumbnailsConfig" v-model="currentSlide" class="slider slider-nav">
                <Slide v-for="item in about_years" :key="item.id" @click="slideTo(item.id - 1)">
                    <h3 class="tp-about-year-nav-title">{{ item.year }}</h3>
                </Slide>
            </Carousel>
        </div>
        <div class="tp-about-year-box">
            <div class="container">
                <div class="row align-items-center">
                    <Carousel v-bind="testimonialConfig" v-model="currentSlide" class="slider slider-for">
                        <Slide v-for="(item) in slider_data" :key="item.id" class="tp-about-year-inner">
                            <div class="row align-items-center">
                                <div class="col-lg-6">
                                    <div class="tp-about-year-thumb">
                                        <img :src="item.image" alt="thumb">
                                    </div>
                                </div>
                                <div class="col-lg-6">
                                    <div class="tp-about-year-content text-start">
                                        <h4 class="tp-about-year-content-title" v-html="item.title"></h4>
                                        <p>{{ item.description }}</p>
                                    </div>
                                </div>
                            </div>
                        </Slide>
                    </Carousel>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import 'vue3-carousel/dist/carousel.css';
import { Carousel, Slide } from 'vue3-carousel';

const currentSlide = ref(0);
const carouselRef = ref<InstanceType<typeof Carousel> | null>(null);

const slideTo = (nextSlide: number) => (currentSlide.value = nextSlide);

// years
const about_years = [{id:1, year:2023}, {id:2, year:2022}, {id:3, year:2024}, {id:4, year:2025}, {id:5, year:2021}];

// slider data 
const slider_data = [
    {
        id: 1,
        image: "/images/our-mission/e1.png",
        title: "Mi Experiencia <br/> Profesional",
        description:
            "Gracias a la formación recibida, hoy me desempeño en el área contable de una empresa privada. La base técnica y el enfoque práctico del instituto fueron clave para insertarme rápidamente en el mercado laboral.",
    },
    {
        id: 2,
        image: "/images/our-mission/e2.png",
        title: "Formación Que <br/> Marca la Diferencia",
        description:
            "Los conocimientos en tributación y finanzas me permitieron trabajar en un estudio contable desde el primer año de egreso. Destaco la calidad docente y el acompañamiento constante durante mi formación.",
    },
    {
        id: 3,
        image: "/images/our-mission/e3.png",
        title: "Crecimiento <br/> y Desarrollo Profesional",
        description:
            "La preparación en contabilidad y análisis financiero me dio seguridad para asumir responsabilidades en el sector público. Hoy aplico lo aprendido con ética y compromiso profesional.",
    },
    {
        id: 4,
        image: "/images/our-mission/e4.png",
        title: "Aprendizaje <br/> Aplicado a la Realidad",
        description:
            "La enseñanza práctica y el uso de herramientas informáticas contables facilitaron mi desempeño laboral. Actualmente trabajo en el área financiera de una empresa regional.La enseñanza práctica y el uso de herramientas informáticas contables facilitaron mi desempeño laboral. Actualmente trabajo en el área financiera de una empresa regional.",
    },
    {
        id: 5,
        image: "/images/our-mission/e5.png",
        title: "Impulso Para <br/> Emprender",
        description:
            "El instituto no solo me brindó conocimientos técnicos, sino también confianza para ejercer de manera independiente. Hoy ofrezco servicios contables a pequeñas empresas y emprendedores.",
    },
];


const testimonialConfig = {
    itemsToShow: 1,
    wrapAround: false,
};

const thumbnailsConfig = {
    itemsToShow: 3,
    wrapAround: true,
    gap: 15,
    breakpoints: {
        // 400px and up
        400: {
            itemsToShow: 2,
        },
        // 500px and up
        500: {
            itemsToShow: 3,
        },
        // 700px and up
        700: {
            itemsToShow: 3,
        },
    },
};

</script>


<style scoped>
.egresados-simple{
  position: absolute;
  top: 40px;              /* más arriba */
  left: 50%;
  transform: translateX(-50%);
  font-size: 78px;        /* más grande */
  font-weight: 900;
  color: #ffffff;         /* blanco */
  margin: 0;
  z-index: 10;
  text-align: center;
}
</style>
