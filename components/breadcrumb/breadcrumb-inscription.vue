<template>
  <section class="tp-breadcrumb__area pt-160 pb-150 p-relative z-index-1 fix">
    <div
      class="tp-breadcrumb__bg overlay"
      :style="{ backgroundImage: 'url(/images/breadcrumb/contaportada.jpeg)' }"
    ></div>

    <div class="container">
      <div class="row align-items-center">
        <div :class="admission ? 'col-lg-8 col-md-10' : 'col-sm-12'">
          <div class="tp-breadcrumb__content">
            
            <div v-if="!admission" class="tp-breadcrumb__list inner-after">
              <span class="white">
                <nuxt-link to="/">
                  <svg-home />
                </nuxt-link>
              </span>
              <span class="white">{{ subtitle }}</span>
            </div>

            <div v-if="admission" class="d-flex align-items-center flex-wrap gap-3 mb-4">
              <span class="badge border border-light text-white px-3 py-2 rounded-pill" style="background: rgba(255, 255, 255, 0.15); font-weight: 500;">
                Convocatoria 2026
              </span>
              <span class="badge border border-light text-white px-3 py-2 rounded-pill d-flex align-items-center gap-2" style="background: rgba(255, 255, 255, 0.15); font-weight: 500;">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>
                Inscripciones abiertas
              </span>
            </div>

            <h3 class="tp-breadcrumb__title color text-white mb-3" :style="admission ? 'font-size: 3.5rem; font-weight: 700;' : ''">
              <template v-if="admission">
                Admisión <span style="color: #f59e0b;">2026</span>
              </template>
              <template v-else>
                {{ title }}
              </template>
            </h3>

            <p v-if="admission" class="text-white mb-5" style="font-size: 1.15rem; max-width: 600px; line-height: 1.6;">
              {{ subtitle }}
            </p>

            <div v-if="admission" class="mt-4">
              <a href="#programas-estudio" class="btn px-4 py-3 rounded-3 d-inline-flex align-items-center gap-2 shadow-sm" style="background-color: #e11d48; border: none; font-weight: 600; color: white;">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><polyline points="12 16 16 12 12 8"></polyline><line x1="8" y1="12" x2="16" y2="12"></line></svg>
                Postular ahora
              </a>
            </div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  title: string, 
  subtitle: string, 
  admission?: boolean
}>()
</script>