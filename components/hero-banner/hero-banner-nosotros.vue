<template>
    <div class="tp-hero-6-area tp-hero-2-bg fix">

        <div class="container custom-container-1300">
            <div class="tp-hero-6-wrap">
                <div class="row align-items-end">
                    
                    <!-- COLUMNA TEXTO -->
                    <div class="col-xxl-7 col-xl-6 col-lg-7 col-md-12">
                        <div class="tp-hero-6-content">

                            <span class="tp-hero-6-subtitle wow fadeInUp" data-wow-delay=".3s">
                                Instituto de Educación Superior Tecnológico Público
                            </span>

                            <h2 class="tp-hero-6-title wow fadeInUp" data-wow-delay=".5s">
                                IESTP <span>Ayaviri</span>
                                <br>Comprometidos con la formación
                                <br>técnica y el desarrollo regional
                            </h2>

                            <p class="wow fadeInUp" data-wow-delay=".7s">
                                Le damos la bienvenida a nuestro portal institucional.
                                Desde nuestra creación, somos referente en educación tecnológica 
                                en la provincia de Melgar y la región Puno, formando profesionales 
                                técnicos con calidad académica, valores y responsabilidad social.
                            </p>

                            <!-- BOTÓN + DIRECTOR -->
                            <div class="tp-hero-6-btn-box d-flex align-items-center wow fadeInUp" data-wow-delay=".9s">
                                
                                <div class="tp-hero-6-btn">
                                    <a class="tp-btn-inner" href="javascript:void(0)">
                                        Mensaje Institucional
                                        <span>
                                            <svg-arrow-right-four />
                                        </span>
                                    </a>
                                </div>

                                <div style="margin-left: 30px;">
                                    <p style="margin:0; font-weight:600;">
                                        CPC. Jesús Manuel Aquino Cutipa
                                    </p>
                                    <span style="font-size:14px; opacity:.8;">
                                        Director General
                                    </span>
                                </div>

                            </div>

                        </div>
                    </div>

                    <!-- COLUMNA IMAGEN -->
                    <div class="col-xxl-5 col-xl-4 col-lg-5 col-md-6">
                        <div class="tp-hero-6-wrap p-relative wow fadeInUp" data-wow-delay=".5s">
                            <div class="tp-hero-6-bg"></div>

                            <div class="tp-hero-6-shape">
                                <div class="shape-1">
                                    <img src="/images/hero/home-6/hero-6-thumb-shape-1.png" alt="shape">
                                </div>
                                <div class="shape-2">
                                    <img src="/images/hero/home-6/hero-6-thumb-shape-2.png" alt="shape">
                                </div>
                                <div class="shape-3">
                                    <img src="/images/hero/home-6/hero-6-thumb-shape-3.png" alt="shape">
                                </div>
                            </div>
                        </div>
                    </div>

                </div>

                <div class="tp-hero-6-thumb">
                    <img src="/images/hero/home-6/hero-nosotros.png" alt="">
                </div>

            </div>
        </div>

        <div class="tp-hero-2-shape">
            <div class="tp-hero-2-shape-2">
                <img src="/images/hero/hero-6-shape-2.png" alt="">
            </div>
            <div class="tp-hero-2-shape-3">
                <img src="/images/hero/hero-2-shape-3.png" alt="">
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
// Ya no usamos video
</script>

<style scoped>
/* Mantengo tu estructura limpia sin el modal de video */

/* ======================================
   COLOR INSTITUCIONAL ROJO
   ====================================== */

:root {
  --tp-theme-color: #b00020; /* rojo institucional */
}

/* Títulos */
.tp-hero-6-title span {
  color: #b00020 !important;
}

/* Botón */
.tp-btn-inner {
  background-color: #b00020 !important;
  border-color: #b00020 !important;
}

.tp-btn-inner:hover {
  background-color: #8c001a !important;
  border-color: #8c001a !important;
}

/* Íconos activos o detalles */
.tp-hero-6-subtitle svg {
  color: #b00020 !important;
}

</style>
