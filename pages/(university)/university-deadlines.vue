<template>
    <div>
        <nuxt-layout name="layout-eight">

            <!-- breadcrumb area start -->
            <breadcrumb-one title="Cronograma de admisión" subtitle="Admisión" :admission="true" />
            <!-- breadcrumb area end -->

            <!-- deadline area start -->
            <deadline-area />
            <!-- deadline area end -->

<program-three />

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University Deadlines - Acadia" });
</script>
