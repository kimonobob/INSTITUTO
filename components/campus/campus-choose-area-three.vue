<template>
    <section class="tp-campus-choose-area pt-120 pb-80 grey-bg">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="tp-campus-choose-wrapper text-center">
                        <div class="tp-campus-choose-btn">
                            <p>Misión y valores</p>
                            <div class="tp-campus-choose-content mb-10">
                                <h2 class="tp-campus-choose-title">
                                    Formamos profesionales técnicos <br />
                                    con calidad, ética y compromiso con <br />
                                    el desarrollo de nuestra región.
                                </h2>
                            </div>
                            <a href="#">
                                <span><svg-arrow-down-three /></span>
                            </a>
                        </div>
                    </div>
                </div>

                <div v-for="(item, index) in chooseData" :key="item.id" class="col-lg-3 col-md-6"
                    :class="{ 'col-lg-6': index === 1 }">
                    <div :class="['tp-mission-valus-thumb mb-30', item.class]">
                        <img :src="item.imgSrc" alt="" />
                        <div class="tp-mission-valus-content">
                            <h4 class="tp-mission-valus-title">{{ item.title }}</h4>
                            <p v-html="item.description"></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>


<script setup lang="ts">
interface ChooseData {
    id: number;
    title: string;
    description: string;
    imgSrc: string;
    class?: string;
}

const chooseData: ChooseData[] = [
    {
        id: 1,
        title: "Visión",
        description:
            "“Somos un Instituto de Educación Superior Tecnológico Público que forma profesionales técnicos competitivos, emprendedores y éticos, mediante una educación de calidad por competencias, para incorporarlos a las actividades del desarrollo productivo de la Región”.",
        imgSrc: "/images/our-mission/mission/mission-thumb-1.jpg",
    },
    {
        id: 2,
        title: "Misión",
        description:
            "“Al 2028, ser un Instituto de Educación Superior, líder a nivel macro regional en formación de profesionales técnicos con formación integral, emprendedores, con identidad social, comprometidos con el medio ambiente y el desarrollo de la Región”",
        imgSrc: "/images/our-mission/mission/mission-thumb-2.jpg",
        class: "main pt-100 mb-30 pl-125",
    },
    {
  id: 3,
  title: "Valores",
  description: `
    <ul class="values-list">
      <li>Ética y responsabilidad</li>
      <li>Compromiso institucional</li>
      <li>Respeto y trabajo en equipo</li>
      <li>Excelencia académica</li>
      <li>Innovación y mejora continua</li>
    </ul>
  `,
  imgSrc: "/images/our-mission/mission/mission-thumb-3.jpg",
},

];
</script>