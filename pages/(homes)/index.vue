<template>
    <div>
        <nuxt-layout name="layout-one">

            <!-- hero area start -->
            <hero-banner-one />
            <!-- hero area end -->

            <!-- service area start -->
            <service-one />
            <!-- service area end -->

            <!-- about area start -->
            <about-one />
            <!-- about area end -->

            <!-- counter area start -->
            <counter-three />
            <!-- counter area end -->

            <!-- program area start -->
            <plan-area />
            <!-- program area end -->

            <!-- event area start -->
            <brand-area spacing="pt-120 pb-120"/>
            <!-- event area end -->
          
            <!-- testimonial area start -->
            <testimonial-three />
            <!-- testimonial area end -->

            <!-- blog area start -->
            <blog-three />
            <!-- blog area end -->

            <!-- instagram area start -->
            <instagram-area />
            <!-- instagram area end -->

            <!-- cta area start -->
            <cta-one />
            <!-- cta area end -->

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "INSTITUTO DE EDUCACIÓN SUPERIOR TECNOLÓGICO PÚBLICO AYAVIRI" });
</script>
