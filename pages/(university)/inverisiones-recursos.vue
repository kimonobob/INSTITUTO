<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-one title="Inversiones y Recursos Académicos" subtitle="Transparencia" />
      <!-- breadcrumb area end -->

      <!-- Inversiones y recursos start -->
      <section class="tp-course-requrement-area grey-bg pt-100 pb-80">
        <div class="container">
          <div class="row">
            <!-- MAIN -->
            <div class="col-lg-9">
              <div class="tp-course-requrement-wrapper inv-wrap">

                <!-- Header -->
                <div class="inv-hero">
                  <div>
                    <span class="inv-kicker">Transparencia</span>
                    <h3 class="tp-course-requrement-title inv-title">Inversiones y Recursos Académicos</h3>
                    <p class="inv-subtitle">
                      Información referencial sobre mejoras, equipamiento y recursos destinados a fortalecer el proceso de enseñanza–aprendizaje.
                    </p>
                  </div>

                  <div class="inv-mini">
                    <div class="mini-item">
                      <span class="mini-label">Actualización</span>
                      <span class="mini-value">Progresiva</span>
                    </div>
                    <div class="mini-item">
                      <span class="mini-label">Formato</span>
                      <span class="mini-value">Resumen</span>
                    </div>
                  </div>
                </div>

                <!-- Cards -->
                <div class="inv-grid">
                  <article v-for="c in cards" :key="c.id" class="inv-card">
                    <div class="inv-card-top">
                      <div class="inv-ico" aria-hidden="true">
                        <span v-html="c.icon"></span>
                      </div>
                      <div>
                        <h4 class="inv-card-title">{{ c.title }}</h4>
                        <p class="inv-card-desc">{{ c.description }}</p>
                      </div>
                    </div>

                    <div class="inv-card-foot">
                      <span class="inv-pill">{{ c.tag }}</span>
                      <span class="inv-pill inv-pill--soft">{{ c.year }}</span>
                    </div>
                  </article>
                </div>

                <!-- Listado simple (para luego enlazar PDFs) -->
                <div class="inv-list">
                  <div class="inv-list-head">
                    <h4 class="inv-list-title">Publicaciones</h4>
                    <p class="inv-list-sub">
                      Cuando tengas los documentos, agrega la ruta en el script y se habilitará “Descargar”.
                    </p>
                  </div>

                  <div class="inv-items">
                    <div v-for="d in docs" :key="d.id" class="inv-item">
                      <div class="inv-item-left">
                        <div class="inv-doc-ico" aria-hidden="true">
                          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M14 2H7a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8l-5-6Z"
                              stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
                            <path d="M14 2v6h6" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
                            <path d="M8 13h8M8 17h6" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
                          </svg>
                        </div>

                        <div class="inv-item-text">
                          <p class="inv-item-name">{{ d.title }}</p>
                          <p class="inv-item-note">{{ d.note }}</p>
                        </div>
                      </div>

                      <div class="inv-item-right">
                        <button
                          v-if="!d.url"
                          class="inv-btn inv-btn--disabled"
                          type="button"
                          disabled
                          aria-disabled="true"
                        >
                          Próximamente
                        </button>

                        <a
                          v-else
                          class="inv-btn"
                          :href="d.url"
                          download
                          target="_blank"
                          rel="noopener"
                        >
                          Descargar <span aria-hidden="true">↓</span>
                        </a>
                      </div>
                    </div>
                  </div>
                </div>

              </div>
            </div>

            <!-- SIDEBAR -->
            <div class="col-lg-3">
              <div class="tp-course-requrement-widget-box">

                <div class="tp-course-requrement-widget mb-30">
                  <div class="tp-course-requrement-widget-content">
                    <nuxt-link href="/documentos">Documentos</nuxt-link>
                    <nuxt-link href="/estadisticas">Estadísticas</nuxt-link>
                    <nuxt-link href="/licenciamiento">Licenciamiento</nuxt-link>
                    <nuxt-link href="/contacto">Contacto</nuxt-link>
                  </div>
                </div>

                <div class="tp-course-requrement-widget-btn mb-30">
                  <nuxt-link class="tp-btn btn-1 w-100 text-center" href="/university-request-info">
                    Solicitar información
                  </nuxt-link>
                  <nuxt-link class="tp-btn btn-2 w-100 text-center" href="/university-apply">
                    Postular ahora
                  </nuxt-link>
                </div>

                <div class="tp-course-requrement-widget-contact mb-30">
                  <h4 class="tp-course-requrement-widget-contact-title">Contacto</h4>
                  <p>Ayaviri, Melgar – Puno</p>
                  <a href="mailto:informes@iestpayaviri.edu.pe"><span><svg-email-one /></span> informes@iestpayaviri.edu.pe</a>
                  <a href="tel:+51000000000"><span><svg-phone /></span> +51 000 000 000</a>
                </div>

                <div class="tp-course-requrement-widget-faq">
                  <h4 class="tp-course-requrement-widget-faq-title">¿Necesitas ayuda?</h4>
                  <p>Revisa nuestras <nuxt-link href="/faq">Preguntas frecuentes</nuxt-link></p>
                  <div class="tp-course-requrement-widget-faq-thumb">
                    <img src="/images/history/undergraduate/course-contact-bg.png" alt="">
                  </div>
                </div>

              </div>
            </div>

          </div>
        </div>
      </section>
      <!-- Inversiones y recursos end -->

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "Inversiones y Recursos Académicos - IESTP" });

type Card = {
  id: number;
  title: string;
  description: string;
  tag: string;
  year: string;
  icon: string;
};

type Doc = {
  id: number;
  title: string;
  note: string;
  url?: string; // futuro: ruta del PDF
};

const cards = ref<Card[]>([
  {
    id: 1,
    title: "Equipamiento y laboratorios",
    description: "Adquisición y mejora de herramientas, equipos y materiales de práctica.",
    tag: "Recursos",
    year: "2024–2025",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M4 7h16v10H4V7Z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M8 17v3h8v-3" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M7 10h10" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
      </svg>
    `,
  },
  {
    id: 2,
    title: "Infraestructura académica",
    description: "Mantenimiento y acondicionamiento de ambientes para el aprendizaje.",
    tag: "Mejoras",
    year: "2024–2025",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M4 20V10l8-5 8 5v10" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
        <path d="M9 20v-7h6v7" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    `,
  },
  {
    id: 3,
    title: "Recursos educativos",
    description: "Materiales y recursos para fortalecer las actividades de formación.",
    tag: "Académico",
    year: "2024–2025",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M4 19V6a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v13" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M4 19a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M8 8h8M8 12h8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
      </svg>
    `,
  },
  {
    id: 4,
    title: "Conectividad y soporte",
    description: "Acciones para fortalecer conectividad, soporte y herramientas digitales.",
    tag: "Tecnología",
    year: "2024–2025",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M5 12a7 7 0 0 1 14 0" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
        <path d="M8.5 12a3.5 3.5 0 0 1 7 0" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
        <path d="M12 12v8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
      </svg>
    `,
  },
]);

const docs = ref<Doc[]>([
  {
    id: 1,
    title: "Resumen de inversiones institucionales",
    note: "Documento referencial (por publicar)",
    url: "",
  },
  {
    id: 2,
    title: "Inventario de equipamiento académico",
    note: "Actualización progresiva",
    url: "",
  },
  {
    id: 3,
    title: "Reporte de mantenimiento y mejoras",
    note: "Ambientes académicos",
    url: "",
  },
]);
</script>

<style scoped>
/* ===== Inversiones y Recursos - Simple, moderno y elegante ===== */
.inv-wrap {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* Hero simple */
.inv-hero {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 14px;
  padding: 18px;
  border-radius: 22px;
  border: 1px solid var(--line);
  background: linear-gradient(180deg, rgba(255,255,255,0.92), rgba(255,255,255,0.70));
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  margin-bottom: 14px;
  position: relative;
  overflow: hidden;
}

.inv-hero::after {
  content: "";
  position: absolute;
  top: -60px;
  right: -60px;
  width: 220px;
  height: 220px;
  border-radius: 50%;
  background: rgba(177, 4, 14, 0.10);
}

.inv-kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.inv-title {
  margin: 8px 0 6px;
  font-size: 32px;
  font-weight: 950;
  letter-spacing: -0.03em;
  color: var(--text);
}

.inv-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
  max-width: 70ch;
}

.inv-mini {
  display: grid;
  gap: 10px;
  align-content: start;
  min-width: 180px;
  position: relative;
  z-index: 1;
}

.mini-item {
  border-radius: 18px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(255,255,255,0.90);
  padding: 10px 12px;
}

.mini-label {
  display: block;
  font-size: 11px;
  font-weight: 950;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: rgba(15, 23, 42, 0.70);
}

.mini-value {
  display: block;
  margin-top: 4px;
  font-size: 14px;
  font-weight: 1000;
  color: var(--text);
}

/* Cards */
.inv-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 14px;
  margin-bottom: 14px;
}

.inv-card {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  padding: 16px;
  transition: transform 0.12s ease, box-shadow 0.12s ease;
}

.inv-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 18px 65px rgba(2, 6, 23, 0.10);
}

.inv-card-top {
  display: grid;
  grid-template-columns: 54px 1fr;
  gap: 12px;
  align-items: start;
}

.inv-ico {
  width: 54px;
  height: 54px;
  border-radius: 18px;
  border: 1px solid rgba(177, 4, 14, 0.16);
  background: var(--soft);
  color: var(--brand);
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.inv-card-title {
  margin: 0 0 6px;
  font-size: 15px;
  font-weight: 1000;
  color: var(--text);
  letter-spacing: -0.01em;
}

.inv-card-desc {
  margin: 0;
  color: var(--muted);
  font-size: 13px;
  line-height: 1.35;
}

.inv-card-foot {
  margin-top: 12px;
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: center;
}

.inv-pill {
  display: inline-flex;
  align-items: center;
  padding: 7px 10px;
  border-radius: 999px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(2, 6, 23, 0.03);
  font-weight: 950;
  font-size: 12px;
  color: rgba(15, 23, 42, 0.80);
}

.inv-pill--soft {
  background: rgba(177, 4, 14, 0.08);
  border-color: rgba(177, 4, 14, 0.18);
  color: var(--brand);
}

/* Listado simple */
.inv-list {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  overflow: hidden;
}

.inv-list-head {
  padding: 16px;
  border-bottom: 1px solid rgba(15, 23, 42, 0.10);
  background: linear-gradient(135deg, rgba(177, 4, 14, 0.10), rgba(2, 6, 23, 0.02));
}

.inv-list-title {
  margin: 0 0 6px;
  font-size: 16px;
  font-weight: 1000;
  color: var(--text);
}

.inv-list-sub {
  margin: 0;
  font-size: 13px;
  color: var(--muted);
}

.inv-items {
  display: grid;
}

.inv-item {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 12px;
  align-items: center;
  padding: 14px 16px;
  border-bottom: 1px solid rgba(15, 23, 42, 0.08);
}

.inv-item:last-child {
  border-bottom: none;
}

.inv-item-left {
  display: grid;
  grid-template-columns: 48px 1fr;
  gap: 12px;
  align-items: start;
}

.inv-doc-ico {
  width: 48px;
  height: 48px;
  border-radius: 16px;
  border: 1px solid rgba(177, 4, 14, 0.16);
  background: var(--soft);
  color: var(--brand);
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.inv-item-name {
  margin: 0;
  font-weight: 1000;
  color: var(--text);
  font-size: 14px;
  line-height: 1.25;
}

.inv-item-note {
  margin: 6px 0 0;
  color: var(--muted);
  font-size: 12px;
}

.inv-item-right {
  display: flex;
  justify-content: flex-end;
}

.inv-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 14px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--brand), var(--brand2));
  color: #fff;
  font-weight: 950;
  font-size: 13px;
  text-decoration: none;
  border: 1px solid rgba(177, 4, 14, 0.35);
  box-shadow: 0 16px 40px rgba(177, 4, 14, 0.22);
  white-space: nowrap;
}

.inv-btn--disabled {
  background: rgba(2, 6, 23, 0.08);
  border-color: rgba(2, 6, 23, 0.10);
  box-shadow: none;
  color: rgba(15, 23, 42, 0.55);
  cursor: not-allowed;
}

/* Responsive */
@media (max-width: 991px) {
  .inv-hero {
    grid-template-columns: 1fr;
  }
  .inv-title {
    font-size: 28px;
  }
  .inv-grid {
    grid-template-columns: 1fr;
  }
  .inv-item {
    grid-template-columns: 1fr;
  }
  .inv-item-right {
    justify-content: flex-start;
  }
}
</style>
