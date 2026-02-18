<template>
    <div>
        <nuxt-layout name="layout-eight">


            <hero-banner-seven />


<cta-one />

            <!-- campus area start -->

            <!-- campus area end -->

            <!-- counter area start -->
            <university-course-details-area />
            <!-- counter area end -->
            

 <program-three />
           

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University Admission Overview - Acadia" });
</script>
