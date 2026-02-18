<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-one title="TUPA 2024" subtitle="Documentos de Gestión" />
      <!-- breadcrumb area end -->

      <!-- TUPA area start -->
      <section class="tp-course-requrement-area grey-bg pt-100 pb-80">
        <div class="container">
          <div class="row">
            <!-- MAIN -->
            <div class="col-lg-9">
              <div class="tp-course-requrement-wrapper tupa-wrap">

                <!-- Header moderno -->
                <div class="tupa-hero">
                  <div class="tupa-hero-left">
                    <span class="tupa-kicker">Documento institucional</span>
                    <h3 class="tp-course-requrement-title tupa-title">TUPA 2024</h3>
                    <p class="tupa-subtitle">
                      Texto Único de Procedimientos Administrativos. Revisa los conceptos y montos establecidos para los
                      trámites institucionales.
                    </p>
                  </div>

                  <div class="tupa-hero-right">
                    <div class="tupa-search">
                      <span class="tupa-search-ico" aria-hidden="true">⌕</span>
                      <input
                        v-model.trim="query"
                        type="text"
                        placeholder="Buscar concepto..."
                        aria-label="Buscar concepto"
                      />
                    </div>

                    <div class="tupa-meta">
                      <span class="tupa-pill">{{ filteredItems.length }} concepto(s)</span>
                      <span class="tupa-pill tupa-pill--soft">Base: UIT 2024</span>
                    </div>
                  </div>
                </div>

                <!-- Tabla moderna -->
                <div class="tupa-card">
                  <div class="tupa-head">
                    <div class="tupa-th num">N°</div>
                    <div class="tupa-th concept">Concepto</div>
                    <div class="tupa-th amount">Monto</div>
                  </div>

                  <div v-if="filteredItems.length === 0" class="tupa-empty">
                    No se encontraron conceptos con ese criterio.
                  </div>

                  <div v-else class="tupa-body">
                    <article
                      v-for="row in filteredItems"
                      :key="row.id"
                      class="tupa-row"
                    >
                      <div class="tupa-td num">
                        <span class="num-badge">{{ row.id }}</span>
                      </div>

                      <div class="tupa-td concept">
                        <div class="concept-title">{{ row.concept }}</div>
                      </div>

                      <div class="tupa-td amount">
                        <span class="amount-pill">S/ {{ row.amount }}</span>
                      </div>
                    </article>
                  </div>

                  <!-- Footer info -->
                  <div class="tupa-foot">
                    <div class="tupa-foot-left">
                      <h4 class="tupa-foot-title">Base de referencia</h4>
                      <p class="tupa-foot-text">
                        U.I.T. 2024 = <strong>S/ 5,150.00</strong> (D.S. N° 309-2023-EF)
                      </p>
                    </div>

                    <!-- En el futuro: PDF -->
                    <div class="tupa-foot-right">
                      <button class="tupa-btn tupa-btn--disabled" type="button" disabled aria-disabled="true">
                        Descargar PDF (próximamente)
                      </button>
                    </div>
                  </div>
                </div>

                <p class="tupa-note">
                  * Los montos mostrados corresponden al TUPA 2024. Para trámites específicos, validar requisitos en la oficina correspondiente.
                </p>

              </div>
            </div>

            <!-- SIDEBAR -->
            <div class="col-lg-3">
              <div class="tp-course-requrement-widget-box">

                <div class="tp-course-requrement-widget mb-30">
                  <div class="tp-course-requrement-widget-content">
                    <nuxt-link href="/documentos">Documentos de Gestión</nuxt-link>
                    <nuxt-link href="/admision">Admisión</nuxt-link>
                    <nuxt-link href="/programas">Programas de estudio</nuxt-link>
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
      <!-- TUPA area end -->

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "TUPA 2024 - IESTP" });

type TupaRow = {
  id: number;
  concept: string;
  amount: number;
};

const query = ref("");

const tupaItems = ref<TupaRow[]>([
  { id: 1, concept: "Carné institucional", amount: 20 },
  { id: 2, concept: "Duplicado carné institucional", amount: 25 },
  { id: 3, concept: "Derecho de examen de admisión – Carpeta de postulante (Prospecto)", amount: 20 },
  { id: 4, concept: "Inscripción del postulante en modalidad ordinario – IES públicos", amount: 100 },
  { id: 5, concept: "Inscripción del postulante en modalidad ordinario – IES privados", amount: 120 },
  { id: 6, concept: "Inscripción del postulante en modalidad exonerados", amount: 150 },
  { id: 7, concept: "Traslado interno", amount: 200 },
  { id: 8, concept: "Traslado externo", amount: 120 },
  { id: 9, concept: "Matrícula ingresante", amount: 170 },
  { id: 10, concept: "Matrícula ingresante rezagados", amount: 255 },
  { id: 11, concept: "Matrícula ingresante extemporánea", amount: 340 },
  { id: 12, concept: "Matrícula traslado externo e interno", amount: 100 },
]);

const filteredItems = computed(() => {
  const q = query.value.toLowerCase().trim();
  if (!q) return tupaItems.value;
  return tupaItems.value.filter((r) =>
    (String(r.id) + " " + r.concept).toLowerCase().includes(q)
  );
});
</script>

<style scoped>
/* ===== TUPA 2024 - Estilo moderno institucional ===== */
.tupa-wrap {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* Hero */
.tupa-hero {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
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

.tupa-hero::after {
  content: "";
  position: absolute;
  top: -60px;
  right: -60px;
  width: 240px;
  height: 240px;
  border-radius: 50%;
  background: rgba(177, 4, 14, 0.10);
}

.tupa-kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.tupa-title {
  margin: 8px 0 6px;
  font-size: 34px;
  font-weight: 950;
  letter-spacing: -0.03em;
  color: var(--text);
}

.tupa-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
  max-width: 66ch;
}

.tupa-hero-right {
  display: grid;
  gap: 10px;
  align-content: start;
}

.tupa-search {
  display: grid;
  grid-template-columns: 34px 1fr;
  align-items: center;
  border: 1px solid rgba(15, 23, 42, 0.14);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.95);
  padding: 8px 10px;
  box-shadow: 0 12px 30px rgba(2, 6, 23, 0.06);
}

.tupa-search-ico {
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

.tupa-search input {
  border: none;
  outline: none;
  background: transparent;
  color: var(--text);
  font-weight: 750;
  font-size: 14px;
  padding: 0 6px;
}

.tupa-meta {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.tupa-pill {
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

.tupa-pill--soft {
  background: rgba(177, 4, 14, 0.08);
  border-color: rgba(177, 4, 14, 0.18);
  color: var(--brand);
}

/* Card / Tabla */
.tupa-card {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  overflow: hidden;
}

.tupa-head {
  display: grid;
  grid-template-columns: 90px 1fr 190px;
  gap: 12px;
  padding: 14px 16px;
  background: linear-gradient(135deg, rgba(177, 4, 14, 0.10), rgba(2, 6, 23, 0.02));
  border-bottom: 1px solid var(--line);
}

.tupa-th {
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 950;
  color: rgba(15, 23, 42, 0.78);
}

.tupa-th.amount {
  text-align: right;
}

.tupa-body {
  display: grid;
}

.tupa-row {
  display: grid;
  grid-template-columns: 90px 1fr 190px;
  gap: 12px;
  padding: 14px 16px;
  align-items: center;
  border-bottom: 1px solid rgba(15, 23, 42, 0.08);
  transition: background 0.12s ease;
}

.tupa-row:hover {
  background: rgba(177, 4, 14, 0.04);
}

.tupa-row:last-child {
  border-bottom: none;
}

.tupa-td.amount {
  display: flex;
  justify-content: flex-end;
}

.num-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 44px;
  height: 44px;
  border-radius: 16px;
  background: rgba(2, 6, 23, 0.04);
  border: 1px solid rgba(15, 23, 42, 0.10);
  font-weight: 950;
  color: var(--text);
}

.concept-title {
  font-weight: 900;
  color: var(--text);
  font-size: 14px;
  line-height: 1.25;
}

.amount-pill {
  display: inline-flex;
  align-items: center;
  padding: 9px 12px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--brand), var(--brand2));
  color: #fff;
  font-weight: 950;
  font-size: 13px;
  border: 1px solid rgba(177, 4, 14, 0.35);
  box-shadow: 0 14px 35px rgba(177, 4, 14, 0.18);
}

/* Footer dentro de card */
.tupa-foot {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 12px;
  align-items: center;
  padding: 16px;
  border-top: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(2, 6, 23, 0.02);
}

.tupa-foot-title {
  margin: 0 0 4px;
  font-size: 14px;
  font-weight: 950;
  color: var(--text);
}

.tupa-foot-text {
  margin: 0;
  font-size: 13px;
  color: var(--muted);
}

.tupa-btn {
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

.tupa-btn--disabled {
  background: rgba(2, 6, 23, 0.08);
  border-color: rgba(2, 6, 23, 0.10);
  box-shadow: none;
  color: rgba(15, 23, 42, 0.55);
  cursor: not-allowed;
}

.tupa-empty {
  padding: 18px 16px;
  color: rgba(100, 116, 139, 0.95);
  font-weight: 850;
  font-size: 13px;
}

.tupa-note {
  margin: 10px 6px 0;
  color: rgba(100, 116, 139, 0.95);
  font-size: 12px;
}

/* Responsive */
@media (max-width: 991px) {
  .tupa-hero {
    grid-template-columns: 1fr;
  }
  .tupa-title {
    font-size: 28px;
  }
  .tupa-head,
  .tupa-row {
    grid-template-columns: 1fr;
  }
  .tupa-th.amount {
    text-align: left;
  }
  .tupa-td.amount {
    justify-content: flex-start;
  }
  .tupa-foot {
    grid-template-columns: 1fr;
  }
}
</style>
