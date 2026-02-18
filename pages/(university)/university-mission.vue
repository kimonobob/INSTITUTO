<template>
    <div>
        <nuxt-layout name="layout-eight">

            <!-- breadcrumb area start -->
            <breadcrumb-one title="Mission and values" subtitle="Mission and values" />
            <!-- breadcrumb area end -->

            <!-- campus choose area start -->
            <campus-choose-area-three />
            <!-- campus choose area end -->

            <!-- mission area start -->
            <mission-area-two />
            <!-- mission area end -->
            <!-- mission area start -->
            <section class="tp-mission-area grey-bg pb-120">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-6">
                            <div class="tp-mission-warp pr-75">
                                <div class="tp-mission-heading">
                                    <h3 class="tp-mission-title">Nuestra <br> responsabilidad</h3>
                                </div>
                                <div class="tp-mission-improve-box">
                                    <span class="tp-mission-improve-dec">Más del</span>
                                    <h4 class="tp-mission-improve-title">90 <span>%</span></h4>
                                    <p>de nuestros egresados culminan satisfactoriamente su formación y se incorporan <br> al ámbito laboral o continúan su desarrollo profesional.</p>
                                </div>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="tp-mission-wrapper">
                                <div class="tp-mission-desc">
                                    <p>Brindar una formación técnica de calidad, con ética y compromiso social, garantizando el desarrollo integral de nuestros estudiantes y su adecuada inserción en el ámbito laboral.</p>
                                    <p>Promovemos una educación orientada a la excelencia, la innovación y el desarrollo sostenible de nuestra región.</p>
                                </div>
                                <div class="tp-mission-conversation-box p-relative">
                                    <h4 class="tp-mission-conversation-title">¿Qué ofrecemos?</h4>
                                    <p>Infraestructura adecuada, docentes especializados y <br>
                                        acompañamiento permanente durante tu formación profesional.</p>
                                    <div class="tp-mission-conversation-thumb">
                                        <img src="/images/our-mission/mission/mission-mesg.png" alt="">
                                    </div>
                                    <div class="tp-mission-conversation-msg">
                                        <span class="tp-mission-conversation-msg-1">Hola 👋</span>
                                        <span class="tp-mission-conversation-msg-2">Inicia hoy tu camino al éxito.</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </section>
            <!-- mission area end -->

        </nuxt-layout>
    </div>
</template>

<script setup lang="ts">
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "University Mission - Acadia" });
</script>
