<template>
    <div>
        <nuxt-layout name="layout-eight">

            <!-- breadcrumb area start -->
            <breadcrumb-one title="Solicitar Información" subtitle="Admisión" :admission="true" />
            <!-- breadcrumb area end -->

          <form-schedule />

            <!-- plan area start -->
        
            <!-- plan area end -->

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University Schedule - Acadia" });
</script>
