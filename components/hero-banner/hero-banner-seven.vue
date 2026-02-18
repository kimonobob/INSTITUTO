<template>
    <div class="tp-hero-6-area lightblue-bg tp-hero-2-bg fix">
        <div class="container custom-container-1300">
            <div class="tp-hero-6-wrap">
                <div class="row align-items-end">
                    <div class="col-xxl-7 col-xl-6 col-lg-7 col-md-12">
                        <div class="tp-hero-6-content">
                            <span class="tp-hero-6-subtitle wow fadeInUp" data-wow-delay=".3s"><svg-pen-one /> 
                                Convocatoria Abierta
                            </span>
                            <h2 class="tp-hero-6-title wow fadeInUp" data-wow-delay=".5s">Admisión <span>2026 
                                <img class="wow bounceIn" data-wow-duration="1.5s" data-wow-delay=".4s" src="/images/hero/home-6/title-vector.png" alt=""></span> 
                                <br>tu carrera técnica <br> empieza aquí
                            </h2>
                            <p class="wow fadeInUp" data-wow-delay=".7s">
                                Conoce modalidades, requisitos y cronograma para postular a nuestros programas de estudio.
                            </p>
                            <div class="tp-hero-6-btn-box d-flex align-items-center wow fadeInUp" data-wow-delay=".9s">
                                <div class="tp-hero-6-btn">
                                    <nuxt-link class="tp-btn-inner" href="/course-with-filter">Información General
                                        <span>
                                            <svg-arrow-right-four />
                                        </span>
                                    </nuxt-link>
                                </div>
                              <div class="tp-hero-6-video">
                                    <a 
                                    @click.prevent="showVideo = true" 
                                    class="video-border-animation popup-video" 
                                    href="#"
                                    >
                                    <span>
                                        <svg-video-play-three />
                                    </span>
                                    </a>

                                    <div v-if="showVideo" class="video-modal">
                                    <div class="video-modal__overlay" @click="showVideo = false"></div>
                                    
                                    <div class="video-modal__content">
                                        <button class="video-modal__close" @click="showVideo = false">×</button>
                                        
                                        <div class="video-wrapper">
                                        <iframe 
                                            width="100%" 
                                            height="100%" 
                                            src="https://www.youtube.com/embed/QSN6otyYPmE?autoplay=1&rel=0" 
                                            title="YouTube video" 
                                            frameborder="0" 
                                            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                                            allowfullscreen
                                        ></iframe>
                                        </div>
                                    </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-xxl-5 col-xl-4 col-lg-5 col-md-6">
                        <div class="tp-hero-6-wrap p-relative wow fadeInUp" data-wow-delay=".5s">
                            <div class="tp-hero-6-bg"></div>
                            <div class="tp-hero-6-shape">
                                <div class="shape-1"><img src="/images/hero/home-6/hero-6-thumb-shape-1.png" alt="shape">
                                </div>
                                <div class="shape-2"><img src="/images/hero/home-6/hero-6-thumb-shape-2.png" alt="shape">
                                </div>
                                <div class="shape-3"><img src="/images/hero/home-6/hero-6-thumb-shape-3.png" alt="shape">
                                </div>
                            </div>

                        </div>
                    </div>
                </div>
                <div class="tp-hero-6-thumb">
                    <img src="/images/hero/home-6/hero-6-thumb.png" alt="">
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

    <!-- video popup start -->
    <modal-video />
    <!-- video popup end -->
</template>

<script setup lang="ts">
const {playVideo} = useVideoPopup();
import { ref } from 'vue'

const showVideo = ref(false)
</script>

import { ref } from 'vue'

const showVideo = ref(false)

<style scoped>
.video-modal {
  position: fixed;
  inset: 0;
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
}

.video-modal__overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.8);
}

.video-modal__content {
  position: relative;
  width: 90%;
  max-width: 960px;
  aspect-ratio: 16 / 9;
  background: #000;
  border-radius: 8px;
  overflow: hidden;
}

.video-modal__close {
  position: absolute;
  top: -45px;
  right: 0;
  font-size: 42px;
  color: white;
  background: none;
  border: none;
  cursor: pointer;
  line-height: 1;
}

.video-wrapper {
  width: 100%;
  height: 100%;
}
</style>