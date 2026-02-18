<template>
    <div>
        <nuxt-layout name="layout-eight">

            <!-- breadcrumb area start -->
            <breadcrumb-one title="History" subtitle="History" />
            <!-- breadcrumb area end -->

            <!-- campus choose area start -->
            <section class="tp-campus-choose-area pt-120 pb-90 grey-bg">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="tp-campus-choose-wrapper text-center">
                                <div class="tp-campus-choose-btn">
                                    <p>Reseña Histórica</p>
                                    <a href="#down">
                                        <span><svg-arrow-down-five /></span>
                                    </a>
                                </div>
                                <div class="tp-campus-choose-content mb-10">
                                    <h2 class="tp-campus-choose-title">Desde su creación, nuestra institución nació como respuesta a la necesidad de educación superior tecnológica en la provincia de Melgar, contribuyendo al desarrollo académico y profesional de la región.
                                    </h2>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <!-- campus choose area end -->

            <!-- history area start -->
            <section class="tp-history-area grey-bg pb-120">
                <div class="container">
                    <div id="down" class="tp-history-box-wrapper p-relative">
                        <div v-for="(item, index) in historyData" :key="item.id" :class="['tp-history-box p-relative',item.overlayClass,index !== historyData.length - 1 ? 'mb-180' : '']">
                            <div class="row align-items-center">
                                <div class="col-lg-2">
                                    <div class="tp-history-year">
                                        <h5 class="tp-history-year-title">{{ item.year }}</h5>
                                    </div>
                                </div>
                                <template v-if="item.thumbPosition === 'left'">
                                    <div class="col-lg-5">
                                        <div class="tp-history-item-thumb-left">
                                            <img :src="item.imgSrc" alt="history-thumbnail"/>
                                        </div>
                                    </div>
                                    <div class="col-lg-5">
                                        <div class="tp-history-item-content">
                                            <h2 class="tp-history-title">{{ item.title }}</h2>
                                            <p v-html="item.description"></p>
                                        </div>
                                    </div>
                                </template>
                                <template v-else>
                                    <div class="col-lg-5">
                                        <div class="tp-history-item-content-left">
                                            <h2 class="tp-history-title">{{ item.title }}</h2>
                                            <p v-html="item.description"></p>
                                        </div>
                                    </div>
                                    <div class="col-lg-5">
                                        <div class="tp-history-item-thumb-right">
                                            <img :src="item.imgSrc" alt="history-thumbnail"/>
                                        </div>
                                    </div>
                                </template>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <!-- history area end -->

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University History - Acadia" });


// history data
const historyData = [
  {
    id: 1,
    year: "1981",
    imgSrc: "/images/history/history-thumb-1.jpg",
    title: "Inicio de actividades",
    description:
      "Se inician las actividades académicas en Ayaviri como respuesta a la necesidad de educación superior tecnológica en la provincia de Melgar, orientada a la formación profesional técnica y al desarrollo regional.",
    thumbPosition: "left",
    overlayClass: "overlay-1",
  },
  {
    id: 2,
    year: "1984",
    imgSrc: "/images/history/history-thumb-2.jpg",
    title: "Creación y formalización institucional",
    description:
      "La institución se formaliza mediante norma correspondiente, consolidando su organización administrativa y académica para brindar servicios educativos con mayor alcance y continuidad.",
    thumbPosition: "right",
    overlayClass: "",
  },
  {
    id: 3,
    year: "1989",
    imgSrc: "/images/history/history-thumb-3.jpg",
    title: "Reconocimiento como instituto",
    description:
      "Se consolida el reconocimiento institucional, fortaleciendo su identidad y proyección educativa, así como la estructura de gestión académica para el crecimiento progresivo de la oferta formativa.",
    thumbPosition: "left",
    overlayClass: "",
  },
  {
    id: 4,
    year: "1991",
    imgSrc: "/images/history/history-thumb-4.jpg",
    title: "Primeros programas de estudio",
    description:
      "Se organizan y fortalecen los programas de estudio iniciales, priorizando la formación técnica con enfoque práctico, articulada a la demanda productiva y de servicios de la región.",
    thumbPosition: "right",
    overlayClass: "overlay-2",
  },
  {
    id: 5,
    year: "1993",
    imgSrc: "/images/history/history-thumb-1.jpg",
    title: "Infraestructura y equipamiento",
    description:
      "Se impulsa la mejora de ambientes académicos, laboratorios y talleres, con equipamiento progresivo que permite reforzar el aprendizaje aplicado y el desarrollo de competencias técnicas.",
    thumbPosition: "left",
    overlayClass: "",
  },
  {
    id: 6,
    year: "1996",
    imgSrc: "/images/history/history-thumb-2.jpg",
    title: "Ampliación de la oferta académica",
    description:
      "Se amplía la oferta de programas y se fortalecen los servicios académicos, promoviendo una formación pertinente, con enfoque de calidad y mejora continua.",
    thumbPosition: "right",
    overlayClass: "",
  },
  {
    id: 7,
    year: "2005",
    imgSrc: "/images/history/history-thumb-3.jpg",
    title: "Consolidación de la gestión académica",
    description:
      "Se consolidan procesos académicos y administrativos: planificación institucional, organización curricular, y acompañamiento al estudiante, reforzando el orden y la eficiencia en la gestión educativa.",
    thumbPosition: "left",
    overlayClass: "",
  },
  {
    id: 8,
    year: "2012",
    imgSrc: "/images/history/history-thumb-4.jpg",
    title: "Modernización y actualización curricular",
    description:
      "Se impulsa la actualización curricular y el fortalecimiento de la formación por competencias, incorporando mejoras en la enseñanza práctica, el uso de tecnologías y la orientación al desempeño profesional.",
    thumbPosition: "right",
    overlayClass: "",
  },
  {
    id: 9,
    year: "2017",
    imgSrc: "/images/history/history-thumb-1.jpg",
    title: "Calidad educativa y acreditación",
    description:
      "Se desarrollan acciones de aseguramiento de la calidad, fortaleciendo estándares académicos, procesos internos y evidencias de mejora, con orientación a la acreditación y la excelencia institucional.",
    thumbPosition: "left",
    overlayClass: "",
  },
  {
    id: 10,
    year: "2018",
    imgSrc: "/images/history/history-thumb-2.jpg",
    title: "Adecuación institucional a IESTP",
    description:
      "Se realiza el proceso de adecuación al marco normativo vigente para Institutos de Educación Superior Tecnológicos Públicos, reforzando la gestión, los servicios académicos y la identidad institucional.",
    thumbPosition: "right",
    overlayClass: "",
  },
  {
    id: 11,
    year: "2020",
    imgSrc: "/images/history/history-thumb-3.jpg",
    title: "Continuidad del servicio educativo",
    description:
      "Se garantizan acciones de continuidad académica y administrativa, priorizando la atención al estudiante, la organización institucional y la mejora de procesos para asegurar el desarrollo del año académico.",
    thumbPosition: "left",
    overlayClass: "",
  },
  {
    id: 12,
    year: "2021",
    imgSrc: "/images/history/history-thumb-4.jpg",
    title: "Fortalecimiento e implementación",
    description:
      "Se impulsan proyectos de fortalecimiento institucional, implementación de recursos, y mejoras en los programas de estudio, reforzando la formación práctica y la empleabilidad de los estudiantes.",
    thumbPosition: "right",
    overlayClass: "",
  },
  {
    id: 13,
    year: "2023",
    imgSrc: "/images/history/history-thumb-1.jpg",
    title: "Proyección institucional y compromiso regional",
    description:
      "La institución reafirma su compromiso con el desarrollo regional, promoviendo una formación profesional técnica pertinente, ética e innovadora, orientada a responder a las necesidades del entorno.",
    thumbPosition: "left",
    overlayClass: "",
  },
  {
    id: 14,
    year: "2024",
    imgSrc: "/images/history/history-thumb-2.jpg",
    title: "Actualidad: mejora continua",
    description:
      "Se continúan fortaleciendo los servicios académicos, infraestructura y gestión institucional, con enfoque en calidad, innovación y acompañamiento permanente al estudiante.",
    thumbPosition: "right",
    overlayClass: "overlay-2",
  },
];


</script>
