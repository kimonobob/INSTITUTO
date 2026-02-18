<template>
    <section class="category-area pb-60">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-xl-8 col-lg-10">
                    <div class="tp-section text-center mb-65">
                        <h5 class="tp-section-5-subtitle mb-10">ÁREAS DE DESEMPEÑO</h5>
                        <h3 class="tp-section-5-title">Campo Laboral</h3>
                    </div>
                </div>
            </div>
            <div class="row wow fadeInUp" data-wow-delay=".3s">
                <div v-for="(item) in category_data" :key="item.id" class="col-xl-3 col-lg-4 col-md-6">
                    <div class="tp-category-5-item mb-60">
                        <div class="tp-category-5-hover"></div>
                        <div class="tp-category-5-thumb">
                            <img :src="item.image" alt="">
                        </div>
                        <div class="tp-category-5-content">
                            <h4 class="tp-category-5-title">
                                <nuxt-link href="">{{ item.title }}
                                   
                                </nuxt-link>
                            </h4>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">

const category_data = [
    {
        id: 1,
        image: "/images/category/lc1.png",
        title: "Estudios contables",
    },
    {
        id: 2,
        image: "/images/category/lc2.png",
        title: "Empresas Privadas",
    },
    {
        id: 3,
        image: "/images/category/lc3.png",
        title: "Consultoría Financiera",
    },
    {
        id: 4,
        image: "/images/category/lc4.png",
        title: "Bancos y Finanzas",
    },
    {
        id: 5,
        image: "/images/category/lc5.png",
        title: "Sector Público",
    },
    {
        id: 6,
        image: "/images/category/lc6.png",
        title: "Auditoría Interna",
    },
    {
        id: 7,
        image: "/images/category/lc7.png",
        title: "Empresas de Seguros",
    },
    {
        id: 8,
        image: "/images/category/lc8.png",
        title: "Profesional Independiente",
    },
];
</script>