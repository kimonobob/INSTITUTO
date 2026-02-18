<template>
    <div>
        <nuxt-layout name="layout-eight">

            <!-- breadcrumb area start -->
            <breadcrumb-one title="Programas de Estudio" subtitle="Conoce nuestros" />
            <!-- breadcrumb area end -->

            <!-- about area start -->
            <about-two spacing="pt-90 pb-90" />
            <!-- about area end -->
             
            <!-- plan area start -->
            <plan-area />
            <!-- plan area end -->

            <why-choose-us />

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "Nuestros programas" });

const undergraduatePrograms = [
    {
        id: 1,
        programs: [
            "Enfermería Técnica",
            "Arquitectura de Plataformas y Servicios TI",
        ],
    },
    {
        id: 2,
        programs: [
            "Producción Agropecuaria",
            "Industrias Alimentarias",
        ],
    },
    {
        id: 3,
        programs: [
            "Contabilidad",
        ],
    },
];
</script>
