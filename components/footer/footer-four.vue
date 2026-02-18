<template>
    <footer>
        <div class="tp-footer-4">
            <div :class="`tp-footer-4-bg ${inner ? 'tp-footer-inner' : ''}`">
                <div class="container">

                    <!-- BOLETÍN -->
                    <div class="tp-footer-4-top">
                        <div class="row">
                            <div class="col-lg-6">
                                <h4 class="tp-footer-4-top-title">
                                    Suscríbete a nuestro boletín institucional <br />
                                    y mantente informado
                                </h4>
                            </div>
                            <div class="col-lg-6">
                                <div class="tp-footer-4-top-form">
                                    <form @submit.prevent="submitForm">
                                        <input type="text" placeholder="Ingresa tu correo electrónico..." v-model="email" />
                                        <button type="submit" class="tp-footer-4-top-btn">
                                            Enviar
                                            <span>
                                                <svg-arrow-right-six clr="currentColor" />
                                            </span>
                                        </button>
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- SECCIÓN PRINCIPAL -->
                    <div class="tp-footer-4-main pt-90 pb-70">
                        <div class="row">

                            <!-- BOTONES -->
                            <div class="col-lg-2 col-sm-6">
                                <div class="tp-footer-widget tp-footer-4-col-1 mb-30">
                                    <div :class="`tp-footer-4-btn ${inner ? 'tp-footer-btn-inner' : ''}`">
                                        <nuxt-link class="active" to="/university-admission-overview">Admisión</nuxt-link>
                                        <nuxt-link to="/contact">Contáctanos</nuxt-link>
                                        <nuxt-link to="/nosotros">La Institución</nuxt-link>
                                    </div>
                                </div>
                            </div>

                            <!-- INSTITUCIÓN -->
                            <div class="col-lg-4 col-sm-6">
                                <div class="tp-footer-widget tp-footer-widget-4 has-border tp-footer-4-col-2 mb-30">
                                    <div class="tp-footer-widget-link">
                                        <ul>
                                            <li><nuxt-link to="/nosotros">Sobre Nosotros</nuxt-link></li>
                                            <li><nuxt-link to="/contabilidad">Programas de Estudio</nuxt-link></li>
                                            <li><nuxt-link to="/documentos-gestion">Transparencia</nuxt-link></li>
                                            <li><nuxt-link to="/blog-standard">Noticias y Comunicados</nuxt-link></li>
                                            <li><nuxt-link to="/libro-reclamaciones">Libro de Reclamaciones</nuxt-link></li>
                                        </ul>
                                    </div>
                                </div>
                            </div>

                            <!-- ACCESOS DIRECTOS -->
                            <div class="col-lg-3 col-sm-6">
                                <div class="tp-footer-widget tp-footer-widget-4 tp-footer-4-col-3 mb-30">
                                    <div class="tp-footer-widget-link">
                                        <ul>
                                            <li><a href="https://eva.iestpayaviri.edu.pe/login/index.php">Aula Virtual</a></li>
                                            <li><a href="https://ayaviri.bibliotecalatina.com/login">Biblioteca Virtual</a></li>
                                            <li><a href="https://sga.iestpayaviri.edu.pe/">Gestión Académica</a></li>
                                            <li><a href="https://bolsa-laboral.iestpayaviri.edu.pe/">Bolsa Laboral</a></li>
                                            <li><a href="https://sga.iestpayaviri.edu.pe/tramite_documentario/registrar">Mesa de Partes</a></li>
                                        </ul>
                                    </div>
                                </div>
                            </div>

                            <!-- INFORMACIÓN DE CONTACTO -->
                            <div class="col-lg-3 col-sm-6">
                                <div class="tp-footer-widget tp-footer-widget-4 tp-footer-4-col-4 mb-30">
                                    <div class="tp-footer-4-info">
                                        <span>
                                            Ayaviri – Provincia de Melgar <br />
                                            Región Puno, Perú
                                        </span>
                                        <div class="tp-footer-4-mail">
                                            <a href="mailto:iestpayaviri@gmail.com">iestpayaviri@gmail.com</a>
                                        </div>
                                        <div class="tp-footer-4-phone">
                                            <a href="tel:+51000000000">+51 000 000 000</a>
                                        </div>
                                    </div>
                                </div>
                            </div>

                        </div>
                    </div>

                </div>
            </div>

            <!-- FOOTER BOTTOM -->
            <div :class="`tp-footer-4-bottom ${inner ? 'tp-footer-inner-bottom' : ''}`">
                <div class="container">
                    <div class="row align-items-center">

                        <div class="col-lg-3 col-md-3">
                            <div class="tp-footer-4-logo tp-header-logo">
                                <nuxt-link to="/">
                                    <img src="/images/logo/logo-white.png" alt="IESTP Ayaviri" />
                                </nuxt-link>
                            </div>
                        </div>

                        <div class="col-lg-6 col-md-5">
                            <div class="tp-footer-4-copyright text-start text-md-center">
                                <span>
                                    © {{ new Date().getFullYear() }} IESTP Ayaviri
                                </span>
                                <span class="span">Todos los derechos reservados</span>
                                <span class="span">Política de Privacidad</span>
                            </div>
                        </div>

                        <div class="col-lg-3 col-md-4">
                            <div class="tp-footer-4-social text-md-end">
                                <social-links />
                            </div>
                        </div>

                    </div>
                </div>
            </div>

        </div>
    </footer>
</template>

<script setup lang="ts">
const email = ref('');

withDefaults(defineProps<{ inner?: boolean }>(), {
    inner: false
})

const submitForm = () => {
    if (email.value) {
        console.log(`Correo enviado: ${email.value}`);
        email.value = '';
    } else {
        console.error('Ingrese un correo válido.');
    }
};
</script>
