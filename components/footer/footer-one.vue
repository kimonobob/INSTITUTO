<template>
    <footer>
      <div :class="`tp-footer-main ${style_2 ? '' : 'grey-bg'} pt-80 pb-55`">
        <div class="container">
          <div class="row">
            <!-- Logo and Contact Section -->
            <div class="col-xl-4 col-lg-3 col-sm-6">
              <div :class="`tp-footer-widget ${style_2 ? 'tp-footer-5-col-1' : 'tp-footer-col-1'} mb-30`">
                <div class="tp-footer-widget-logo mb-20 tp-header-logo">
                  <nuxt-link to="/">
                    <img class="logo-2" src="/images/logo/logo-black-1.png" alt="logo" style="width: 250px; height: auto;">
                    
                  </nuxt-link>
                </div>
                <div class="tp-footer-widget-content">
                  <p>
                    Formando profesionales técnicos con valores, compromiso y vocación de servicio para el desarrollo de la provincia de Melgar y la región Puno.
                  </p>
                </div>
                <div class="tp-footer-contact">
                  <span>¿Tienes consultas? Contáctanos</span>
                  <a href="tel:012345678">+51 000 000 000</a>
                </div>
                <div class="tp-footer-contact-mail">
                  <a href="mailto:acadia@gmail.com">
                    <span>
                      <svg-email-one />
                    </span>
                    iestpayaviri@gmail.com
                  </a>
                </div>
              </div>
            </div>
  
            <!-- About Links Section -->
            <div class="col-xl-2 col-lg-3 col-sm-6">
              <div :class="`tp-footer-widget ${style_2 ? 'tp-footer-5-col-2' : 'tp-footer-col-2'} mb-30`">
                <h4 class="tp-footer-widget-title mb-20">Institución</h4>
                <div class="tp-footer-widget-link">
                  <ul>
                    <li v-for="link in footerLinks.link_one" :key="link.id">
                      <nuxt-link :to="link.link">{{ link.title }}</nuxt-link>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
  
            <!-- Quick Links Section -->
            <div class="col-xl-2 col-lg-2 col-sm-4">
              <div :class="`tp-footer-widget ${style_2 ? 'tp-footer-5-col-3' : 'tp-footer-col-3'} mb-30`">
                <h4 class="tp-footer-widget-title mb-20">Accesos Directos</h4>
                <div class="tp-footer-widget-link">
                  <ul>
                    <li v-for="link in footerLinks.link_two" :key="link.id">
                      <nuxt-link :to="link.link">{{ link.title }}</nuxt-link>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
  
            <!-- Newsletter Section -->
            <div class="col-xl-4 col-lg-4 col-sm-8">
              <div :class="`tp-footer-widget ${style_2 ? 'tp-footer-5-col-4' : 'tp-footer-col-4'} mb-30`">
                <h4 class="tp-footer-widget-title mb-20">Boletín Informativo</h4>
                <div class="tp-footer-newsletter-wrap">
                  <p>Ingresa tu correo electrónico y te enviaremos <br /> información institucional y novedades.</p>
                  <form @submit.prevent>
                    <div class="tp-footer-newsletter-wrapper mb-30">
                      <div :class="`tp-footer-newsletter-input ${style_2 ? 'tp-footer-5-newsletter-input' : ''}`">
                        <input type="email" placeholder="Your email" />
                      </div>
                      <div :class="`${style_2 ? 'tp-footer-5-newsletter-submit' : 'tp-footer-newsletter-submit'}`">
                        <button :class="`${style_2 ? 'tp-btn-4' : 'tp-btn'}`">Subscribe</button>
                      </div>
                    </div>
                  </form>
                  <!-- Footer Social -->
                   <div class="tp-footer-newsletter-social">
                       <social-links/>
                   </div>
                  <!-- Footer Social -->
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
  
      <!-- Footer Bottom Section -->
      <div :class="`${style_2 ? 'tp-footer-5-bottom' : 'tp-footer-bottom'}`">
        <div class="container">
          <div class="row">
            <div class="col-lg-12">
              <div class="tp-footer-copyright text-center">
                <span>
                  © {{ new Date().getFullYear() }} <a href="#">IESTP</a>. Todos los derechos reservados
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </template>
  
  <script setup lang="ts">
  import { footerLinks } from "@/data/footer-links";
  
  const props = defineProps<{style_2?: boolean;}>();
  
  const style_2 = props.style_2 ?? false;
  </script>
  