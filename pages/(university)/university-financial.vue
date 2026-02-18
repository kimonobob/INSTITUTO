<template>
    <div>
        <nuxt-layout name="layout-eight">

            <!-- breadcrumb area start -->
            <breadcrumb-one title="Becas y Apoyos" subtitle="Admisión" :admission="true" />
            <!-- breadcrumb area end -->

            <!-- process area start -->
            <process-three />
            <!-- process area end -->

<program-three />
        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University Financial Aid - Acadia" });


// Financial Aid Data
const financialAidData = [
    {
        id: 1,
        imgSrc: "/images/course/details/financial-thumb-1.jpg",
        title: "Scholarships",
        description:
            "Acadia’s commitment to student success, important scholarship, and creative activity sets it apart from other colleges.",
    },
    {
        id: 2,
        imgSrc: "/images/course/details/financial-thumb-2.jpg",
        title: "Grants",
        description:
            "Your FAFSA will determine what grants you qualify for—both from The Acadia University & from federal and state government.",
    },
    {
        id: 3,
        imgSrc: "/images/course/details/financial-thumb-3.jpg",
        title: "Loans",
        description:
            "Many students have used federal and private loans to fund a quality education that would otherwise be out of reach.",
    },
];
</script>
