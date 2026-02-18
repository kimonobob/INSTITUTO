<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-one title="Documentos de Gestión" subtitle="Transparencia" />
      <!-- breadcrumb area end -->

      <!-- Documentos de Gestión area start -->
      <section class="tp-course-requrement-area grey-bg pt-100 pb-80">
        <div class="container">
          <div class="row">
            <!-- MAIN -->
            <div class="col-lg-9">
              <div class="tp-course-requrement-wrapper docs-wrap">

                <!-- Header moderno -->
                <div class="docs-hero">
                  <div class="docs-hero-left">
                    <span class="docs-kicker">Sobre nuestros</span>
                    <h3 class="tp-course-requrement-title docs-title">Documentos de Gestión</h3>
                    <p class="docs-subtitle">
                      Accede a los documentos institucionales que orientan la gestión académica y administrativa.
                      Aquí podrás consultarlos y, cuando estén disponibles, descargarlos.
                    </p>
                  </div>

                  <div class="docs-hero-right">
                    <div class="docs-search">
                      <span class="docs-search-ico" aria-hidden="true">⌕</span>
                      <input
                        v-model.trim="query"
                        type="text"
                        placeholder="Buscar documento..."
                        aria-label="Buscar documento"
                      />
                    </div>
                    <div class="docs-meta">
                      <span class="docs-pill">{{ filteredDocs.length }} documento(s)</span>
                      <span class="docs-pill docs-pill--soft">Actualizable</span>
                    </div>
                  </div>
                </div>

                <!-- Lista moderna -->
                <div class="docs-card">
                  <div class="docs-head">
                    <div class="docs-head-col">Documentos de Gestión</div>
                    <div class="docs-head-col docs-head-col--right">Acción</div>
                  </div>

                  <div v-if="filteredDocs.length === 0" class="docs-empty">
                    No se encontraron documentos con ese criterio.
                  </div>

                  <div v-else class="docs-body">
                    <article v-for="doc in filteredDocs" :key="doc.id" class="doc-row">
                      <div class="doc-left">
                        <div class="doc-ico" aria-hidden="true">
                          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"
                            xmlns="http://www.w3.org/2000/svg">
                            <path
                              d="M14 2H7a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8l-5-6Z"
                              stroke="currentColor"
                              stroke-width="1.8"
                              stroke-linejoin="round"
                            />
                            <path d="M14 2v6h6" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
                            <path d="M8 13h8M8 17h6" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
                          </svg>
                        </div>

                        <div class="doc-text">
                          <h4 class="doc-name">{{ doc.name }}</h4>
                          <p class="doc-note" v-if="doc.note">{{ doc.note }}</p>
                        </div>
                      </div>

                      <div class="doc-right">
                        <!-- Cuando NO hay ruta -->
                        <button
                          v-if="!doc.url"
                          type="button"
                          class="doc-btn doc-btn--disabled"
                          disabled
                          aria-disabled="true"
                          title="Próximamente disponible"
                        >
                          Próximamente
                        </button>

                        <!-- Cuando ya tenga ruta -->
                        <a
                          v-else
                          class="doc-btn"
                          :href="doc.url"
                          download
                          target="_blank"
                          rel="noopener"
                          :aria-label="`Descargar ${doc.name}`"
                        >
                          Descargar <span class="doc-arrow" aria-hidden="true">↓</span>
                        </a>
                      </div>
                    </article>
                  </div>
                </div>

                <p class="docs-footnote">
                  * Los enlaces de descarga se habilitarán conforme se publiquen los archivos oficiales.
                </p>

              </div>
            </div>

            <!-- SIDEBAR -->
            <div class="col-lg-3">
              <div class="tp-course-requrement-widget-box">

                <div class="tp-course-requrement-widget mb-30">
                  <div class="tp-course-requrement-widget-content">
                    <nuxt-link href="/admision">Admisión</nuxt-link>
                    <nuxt-link href="/programas">Programas de estudio</nuxt-link>
                    <nuxt-link href="/autoridades">Autoridades</nuxt-link>
                    <nuxt-link href="/transparencia">Transparencia</nuxt-link>
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
                  <a href="mailto:informes@iestpayaviri.edu.pe">
                    <span><svg-email-one /></span> informes@iestpayaviri.edu.pe
                  </a>
                  <a href="tel:+51000000000">
                    <span><svg-phone /></span> +51 000 000 000
                  </a>
                </div>

                <div class="tp-course-requrement-widget-faq">
                  <h4 class="tp-course-requrement-widget-faq-title">¿Tienes más preguntas?</h4>
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
      <!-- Documentos de Gestión area end -->

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "Documentos de Gestión - IESTP" });

type DocItem = {
  id: number;
  name: string;
  note?: string;
  url?: string; // ✅ en el futuro agregas la ruta aquí
};

const query = ref("");

/**
 * ✅ Cuando tengas PDFs:
 * - Si están en /public/docs/, usa: url: "/docs/tupa.pdf"
 * - Si es enlace externo, pega la URL completa.
 */
const documents = ref<DocItem[]>([
  { id: 1, name: "Texto Único de Procesos Administrativos (TUPA)", note: "Documento normativo institucional", url: "" },
  { id: 2, name: "Proyecto Educativo Institucional (PEI)", note: "Lineamientos y objetivos institucionales", url: "" },
  { id: 3, name: "Reglamento Institucional (RI)", note: "Normas internas de funcionamiento", url: "" },
  { id: 4, name: "Plan Anual de Trabajo (PAT) – 2022", note: "Planificación anual", url: "" },
  { id: 5, name: "Reglamento de Titulación", note: "Procedimientos y requisitos", url: "" },
  { id: 6, name: "Reglamento de experiencias formativas en situaciones reales de trabajo", note: "Lineamientos de prácticas formativas", url: "" },
  { id: 7, name: "Informe Movimiento económico al 30/09/2025", note: "Corte: 30/09/2025", url: "" },
]);

const filteredDocs = computed(() => {
  const q = query.value.toLowerCase().trim();
  if (!q) return documents.value;
  return documents.value.filter((d) =>
    (d.name + " " + (d.note ?? "")).toLowerCase().includes(q)
  );
});
</script>

<style scoped>
/* ===== Documentos de Gestión - Estilo moderno institucional ===== */
.docs-wrap {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* Hero */
.docs-hero {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 16px;
  padding: 18px;
  border-radius: 22px;
  border: 1px solid var(--line);
  background: linear-gradient(180deg, rgba(255,255,255,0.92), rgba(255,255,255,0.70));
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  position: relative;
  overflow: hidden;
  margin-bottom: 14px;
}

.docs-hero::after {
  content: "";
  position: absolute;
  top: -60px;
  right: -60px;
  width: 240px;
  height: 240px;
  border-radius: 50%;
  background: rgba(177, 4, 14, 0.10);
}

.docs-kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.docs-title {
  margin: 8px 0 6px;
  font-size: 34px;
  font-weight: 950;
  letter-spacing: -0.03em;
  color: var(--text);
}

.docs-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
  max-width: 66ch;
}

.docs-hero-right {
  display: grid;
  gap: 10px;
  align-content: start;
}

.docs-search {
  display: grid;
  grid-template-columns: 34px 1fr;
  align-items: center;
  border: 1px solid rgba(15, 23, 42, 0.14);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.95);
  padding: 8px 10px;
  box-shadow: 0 12px 30px rgba(2, 6, 23, 0.06);
}

.docs-search-ico {
  width: 34px;
  height: 34px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border-radius: 12px;
  background: var(--soft);
  color: var(--brand);
  font-weight: 900;
}

.docs-search input {
  border: none;
  outline: none;
  background: transparent;
  color: var(--text);
  font-weight: 750;
  font-size: 14px;
  padding: 0 6px;
}

.docs-meta {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.docs-pill {
  display: inline-flex;
  align-items: center;
  padding: 8px 12px;
  border-radius: 999px;
  border: 1px solid rgba(15, 23, 42, 0.12);
  background: rgba(2, 6, 23, 0.03);
  color: var(--text);
  font-weight: 900;
  font-size: 12px;
}

.docs-pill--soft {
  background: rgba(177, 4, 14, 0.08);
  border-color: rgba(177, 4, 14, 0.18);
  color: var(--brand);
}

/* Card */
.docs-card {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  overflow: hidden;
}

.docs-head {
  display: grid;
  grid-template-columns: 1fr 210px;
  gap: 12px;
  padding: 14px 16px;
  background: linear-gradient(135deg, rgba(177, 4, 14, 0.10), rgba(2, 6, 23, 0.02));
  border-bottom: 1px solid var(--line);
}

.docs-head-col {
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 950;
  color: rgba(15, 23, 42, 0.78);
}

.docs-head-col--right {
  text-align: right;
}

.docs-body {
  display: grid;
}

.doc-row {
  display: grid;
  grid-template-columns: 1fr 210px;
  gap: 12px;
  padding: 14px 16px;
  align-items: center;
  border-bottom: 1px solid rgba(15, 23, 42, 0.08);
  transition: background 0.12s ease;
}

.doc-row:hover {
  background: rgba(177, 4, 14, 0.04);
}

.doc-row:last-child {
  border-bottom: none;
}

.doc-left {
  display: grid;
  grid-template-columns: 52px 1fr;
  gap: 14px;
  align-items: start;
}

.doc-ico {
  width: 52px;
  height: 52px;
  border-radius: 18px;
  border: 1px solid rgba(177, 4, 14, 0.16);
  background: var(--soft);
  color: var(--brand);
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.doc-name {
  margin: 0;
  font-size: 15px;
  font-weight: 950;
  letter-spacing: -0.01em;
  color: var(--text);
  line-height: 1.25;
}

.doc-note {
  margin: 6px 0 0;
  color: var(--muted);
  font-size: 13px;
  line-height: 1.35;
}

.doc-right {
  display: flex;
  justify-content: flex-end;
}

.doc-btn {
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
  transition: transform 0.12s ease, box-shadow 0.12s ease;
  white-space: nowrap;
}

.doc-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 20px 55px rgba(177, 4, 14, 0.28);
}

.doc-btn--disabled {
  background: rgba(2, 6, 23, 0.08);
  border-color: rgba(2, 6, 23, 0.10);
  box-shadow: none;
  color: rgba(15, 23, 42, 0.55);
  cursor: not-allowed;
}

.doc-arrow {
  font-weight: 1000;
}

.docs-empty {
  padding: 18px 16px;
  color: rgba(100, 116, 139, 0.95);
  font-weight: 850;
  font-size: 13px;
}

.docs-footnote {
  margin: 10px 6px 0;
  color: rgba(100, 116, 139, 0.95);
  font-size: 12px;
}

/* Responsive */
@media (max-width: 991px) {
  .docs-hero {
    grid-template-columns: 1fr;
  }
  .docs-title {
    font-size: 28px;
  }
  .docs-head,
  .doc-row {
    grid-template-columns: 1fr;
  }
  .docs-head-col--right {
    text-align: left;
  }
  .doc-right {
    justify-content: flex-start;
  }
}
</style>
