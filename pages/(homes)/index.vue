<template>
    <div>
        <nuxt-layout name="layout-one">

            <hero-banner-one />
            <service-one />
            <about-one />
            <counter-three />
            <plan-area />
            <brand-area spacing="pt-120 pb-120"/>
            <testimonial-three />
            <blog-three />
            <instagram-area />
            <cta-one />
            </nuxt-layout>

        <transition name="fade-popup">
            <div v-if="showPopup" class="popup-overlay" @click="closePopup">
                <div class="popup-content" @click.stop>
                    
                    <button class="close-popup-btn" @click="closePopup" aria-label="Cerrar comunicado">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
                    </button>
                    
                    <img src="/images/admision/publi.png" alt="Comunicado IESTP Ayaviri" class="img-fluid rounded-4 shadow-lg">
                </div>
            </div>
        </transition>

    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Configuración de la página
definePageMeta({
    layout: false,
});
useSeoMeta({ title: "INSTITUTO DE EDUCACIÓN SUPERIOR TECNOLÓGICO PÚBLICO AYAVIRI" });

// --- LÓGICA DEL POP-UP (COMUNICADO) ---
// Inicia en true para que aparezca automáticamente al cargar la página
const showPopup = ref(true)

// Función para cerrarlo
const closePopup = () => {
    showPopup.value = false
}
</script>

<style scoped>
/* =========================================
   ESTILOS DEL POP-UP AL INICIO
   ========================================= */
.popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(15, 23, 42, 0.85); /* Fondo oscuro con transparencia */
    backdrop-filter: blur(5px); /* Efecto de desenfoque moderno */
    z-index: 999999; /* Nivel altísimo para que cubra el menú de navegación (header) */
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.popup-content {
    position: relative;
    max-width: 600px; /* Tamaño máximo del afiche */
    width: 100%;
    animation: scaleUp 0.4s cubic-bezier(0.16, 1, 0.3, 1); /* Pequeña animación de entrada */
}

.popup-content img {
    width: 100%;
    height: auto;
    border: 3px solid white; /* Borde blanco elegante para resaltarlo */
}

.close-popup-btn {
    position: absolute;
    top: -15px;
    right: -15px;
    background: #e11d48; /* Rojo institucional */
    color: white;
    border: 3px solid white; /* Borde blanco para que destaque */
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: all 0.2s ease;
    z-index: 10;
    box-shadow: 0 4px 10px rgba(0,0,0,0.3);
}

.close-popup-btn:hover {
    background: #be123c;
    transform: scale(1.1);
}

/* Animación de opacidad */
.fade-popup-enter-active,
.fade-popup-leave-active {
    transition: opacity 0.3s ease;
}
.fade-popup-enter-from,
.fade-popup-leave-to {
    opacity: 0;
}

/* Animación de escala para la imagen */
@keyframes scaleUp {
    from {
        opacity: 0;
        transform: scale(0.9);
    }
    to {
        opacity: 1;
        transform: scale(1);
    }
}
</style>