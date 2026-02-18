<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-one title="Estadísticas" subtitle="Transparencia" />
      <!-- breadcrumb area end -->

      <!-- Estadísticas start -->
      <section class="tp-course-requrement-area grey-bg pt-100 pb-80">
        <div class="container">
          <div class="row">
            <!-- MAIN -->
            <div class="col-lg-9">
              <div class="tp-course-requrement-wrapper stats-wrap">

                <!-- Header moderno -->
                <div class="stats-hero">
                  <div class="stats-hero-left">
                    <span class="stats-kicker">Indicadores institucionales</span>
                    <h3 class="tp-course-requrement-title stats-title">Estadísticas</h3>
                    <p class="stats-subtitle">
                      Visualiza indicadores clave de manera dinámica. Puedes cambiar el periodo para comparar resultados.
                    </p>
                  </div>

                  <div class="stats-hero-right">
                    <div class="stats-controls">
                      <label class="stats-label" for="period">Periodo</label>
                      <select id="period" v-model="selectedPeriod" class="stats-select">
                        <option v-for="p in periods" :key="p" :value="p">{{ p }}</option>
                      </select>
                    </div>

                    <div class="stats-pills">
                      <span class="stats-pill">{{ activeStats.length }} indicadores</span>
                      <span class="stats-pill stats-pill--soft">Actualizable</span>
                    </div>
                  </div>
                </div>

                <!-- Cards -->
                <div ref="cardsRoot" class="stats-grid">
                  <article
                    v-for="item in activeStats"
                    :key="item.id"
                    class="stat-card"
                  >
                    <div class="stat-top">
                      <div class="stat-icon" aria-hidden="true">
                        <span v-html="item.icon"></span>
                      </div>

                      <div class="stat-meta">
                        <span class="stat-label">{{ item.label }}</span>
                        <div class="stat-value">
                          <span class="stat-number">{{ formattedValue(item.id) }}</span>
                          <span v-if="item.suffix" class="stat-suffix">{{ item.suffix }}</span>
                        </div>
                      </div>
                    </div>

                    <p class="stat-desc" v-if="item.description">{{ item.description }}</p>

                    <div class="stat-foot">
                      <span class="stat-chip">{{ selectedPeriod }}</span>
                      <span v-if="item.note" class="stat-note">{{ item.note }}</span>
                    </div>
                  </article>
                </div>

                <!-- Mini tabla comparativa -->
                <div class="stats-table">
                  <div class="stats-table-head">
                    <div class="th">Indicador</div>
                    <div class="th right">{{ periods[0] }}</div>
                    <div class="th right">{{ periods[1] }}</div>
                    <div class="th right">Var.</div>
                  </div>

                  <div class="stats-table-body">
                    <div v-for="row in compareRows" :key="row.id" class="tr">
                      <div class="td name">{{ row.label }}</div>
                      <div class="td right">{{ row.p0 }}</div>
                      <div class="td right">{{ row.p1 }}</div>
                      <div class="td right">
                        <span :class="['var', row.diff >= 0 ? 'up' : 'down']">
                          {{ row.diff >= 0 ? "+" : "" }}{{ row.diff }}
                        </span>
                      </div>
                    </div>
                  </div>

                  <p class="stats-footnote">
                    * Valores referenciales (puedes actualizar los datos en el script). Si un indicador no aplica, colócalo en 0.
                  </p>
                </div>

              </div>
            </div>

            <!-- SIDEBAR -->
            <div class="col-lg-3">
              <div class="tp-course-requrement-widget-box">

                <div class="tp-course-requrement-widget mb-30">
                  <div class="tp-course-requrement-widget-content">
                    <nuxt-link href="/documentos">Documentos</nuxt-link>
                    <nuxt-link href="/tupa">TUPA 2024</nuxt-link>
                    <nuxt-link href="/libro-reclamaciones">Libro de reclamaciones</nuxt-link>
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
      <!-- Estadísticas end -->

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { computed, onBeforeUnmount, onMounted, ref, watch } from "vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "Estadísticas - IESTP" });

type StatDef = {
  id: string;
  label: string;
  description?: string;
  note?: string;
  suffix?: string; // %, +, etc.
  icon: string;    // svg inline
};

type PeriodKey = "2024" | "2025";

const periods: PeriodKey[] = ["2024", "2025"];
const selectedPeriod = ref<PeriodKey>("2025");

/**
 * ✅ EDITA AQUÍ tus números reales
 * Puedes agregar más indicadores si deseas.
 */
const stats: StatDef[] = [
  {
    id: "students",
    label: "Estudiantes matriculados",
    description: "Cantidad total de estudiantes registrados en el periodo.",
    note: "Dato anual",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 3l10 6-10 6L2 9l10-6Z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M6 12v6c0 1.5 3 3 6 3s6-1.5 6-3v-6" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
      </svg>
    `,
  },
  {
    id: "programs",
    label: "Programas de estudio",
    description: "Oferta académica vigente.",
    note: "Actual",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M4 19V6a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v13" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M4 19a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M8 8h8M8 12h8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
      </svg>
    `,
  },
  {
    id: "graduates",
    label: "Egresados",
    description: "Total de egresados del periodo.",
    note: "Dato anual",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M2 7l10-4 10 4-10 4L2 7Z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M6 10v6c0 1.7 2.7 3 6 3s6-1.3 6-3v-6" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M22 7v7" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
      </svg>
    `,
  },
  {
    id: "scholarships",
    label: "Becas / apoyos",
    description: "Beneficios y apoyos otorgados en el periodo.",
    note: "Dato anual",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M20 7H4a2 2 0 0 0-2 2v2h20V9a2 2 0 0 0-2-2Z" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M2 11v6a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2v-6" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
        <path d="M12 7V5a2 2 0 0 0-2-2H8a2 2 0 0 0-2 2v2" stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
      </svg>
    `,
  },
  {
    id: "satisfaction",
    label: "Satisfacción del usuario",
    description: "Indicador referencial para seguimiento.",
    note: "Encuesta interna",
    suffix: "%",
    icon: `
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M20 12a8 8 0 1 1-8-8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>
        <path d="M20 4v8h-8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    `,
  },
];

const dataByPeriod: Record<PeriodKey, Record<string, number>> = {
  "2024": {
    students: 820,
    programs: 5,
    graduates: 210,
    scholarships: 65,
    satisfaction: 88,
  },
  "2025": {
    students: 910,
    programs: 5,
    graduates: 245,
    scholarships: 72,
    satisfaction: 90,
  },
};

const activeStats = computed(() => stats);

function getTargetValue(id: string) {
  return dataByPeriod[selectedPeriod.value]?.[id] ?? 0;
}

/** Animación de contadores */
const cardsRoot = ref<HTMLElement | null>(null);
const animatedValues = ref<Record<string, number>>({});
const hasAnimated = ref(false);
let observer: IntersectionObserver | null = null;

function formatNumber(n: number) {
  // enteros con separador
  return new Intl.NumberFormat("es-PE").format(Math.round(n));
}

function formattedValue(id: string) {
  const v = animatedValues.value[id] ?? 0;
  return formatNumber(v);
}

function animateAll() {
  const duration = 900; // ms
  const start = performance.now();

  const from: Record<string, number> = {};
  const to: Record<string, number> = {};

  for (const s of stats) {
    from[s.id] = 0;
    to[s.id] = getTargetValue(s.id);
  }

  function tick(now: number) {
    const t = Math.min(1, (now - start) / duration);
    const eased = 1 - Math.pow(1 - t, 3); // easeOutCubic

    const next: Record<string, number> = {};
    for (const s of stats) {
      next[s.id] = from[s.id] + (to[s.id] - from[s.id]) * eased;
    }
    animatedValues.value = next;

    if (t < 1) requestAnimationFrame(tick);
  }

  requestAnimationFrame(tick);
}

watch(selectedPeriod, () => {
  // reinicia animación en cambio de periodo (si ya se mostró)
  if (hasAnimated.value) animateAll();
});

onMounted(() => {
  // inicializar valores
  const init: Record<string, number> = {};
  for (const s of stats) init[s.id] = 0;
  animatedValues.value = init;

  observer = new IntersectionObserver(
    (entries) => {
      const entry = entries[0];
      if (entry?.isIntersecting && !hasAnimated.value) {
        hasAnimated.value = true;
        animateAll();
      }
    },
    { threshold: 0.18 }
  );

  if (cardsRoot.value) observer.observe(cardsRoot.value);
});

onBeforeUnmount(() => {
  if (observer && cardsRoot.value) observer.unobserve(cardsRoot.value);
  observer = null;
});

/** Tabla comparativa (periodos[0] vs periodos[1]) */
const compareRows = computed(() => {
  const p0 = periods[0];
  const p1 = periods[1];

  return stats.map((s) => {
    const v0 = dataByPeriod[p0]?.[s.id] ?? 0;
    const v1 = dataByPeriod[p1]?.[s.id] ?? 0;
    return {
      id: s.id,
      label: s.label,
      p0: s.suffix ? `${v0}${s.suffix}` : formatNumber(v0),
      p1: s.suffix ? `${v1}${s.suffix}` : formatNumber(v1),
      diff: v1 - v0,
    };
  });
});
</script>

<style scoped>
/* ===== Estadísticas - Estilo moderno institucional ===== */
.stats-wrap {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* Hero */
.stats-hero {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
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

.stats-hero::after {
  content: "";
  position: absolute;
  top: -60px;
  right: -60px;
  width: 240px;
  height: 240px;
  border-radius: 50%;
  background: rgba(177, 4, 14, 0.10);
}

.stats-kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.stats-title {
  margin: 8px 0 6px;
  font-size: 34px;
  font-weight: 950;
  letter-spacing: -0.03em;
  color: var(--text);
}

.stats-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
  max-width: 66ch;
}

.stats-hero-right {
  display: grid;
  gap: 10px;
  align-content: start;
}

.stats-controls {
  display: grid;
  gap: 6px;
}

.stats-label {
  font-size: 12px;
  font-weight: 900;
  color: rgba(15, 23, 42, 0.75);
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

.stats-select {
  width: 100%;
  border-radius: 16px;
  border: 1px solid rgba(15, 23, 42, 0.14);
  background: rgba(255, 255, 255, 0.95);
  padding: 12px 12px;
  outline: none;
  font-weight: 900;
  color: var(--text);
  box-shadow: 0 12px 30px rgba(2, 6, 23, 0.06);
}

.stats-pills {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.stats-pill {
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

.stats-pill--soft {
  background: rgba(177, 4, 14, 0.08);
  border-color: rgba(177, 4, 14, 0.18);
  color: var(--brand);
}

/* Cards grid */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 14px;
  margin-bottom: 14px;
}

.stat-card {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  padding: 16px;
  transition: transform 0.12s ease, box-shadow 0.12s ease;
}

.stat-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 18px 65px rgba(2, 6, 23, 0.10);
}

.stat-top {
  display: grid;
  grid-template-columns: 54px 1fr;
  gap: 12px;
  align-items: center;
}

.stat-icon {
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

.stat-label {
  display: block;
  color: rgba(15, 23, 42, 0.70);
  font-size: 12px;
  font-weight: 900;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

.stat-value {
  display: flex;
  align-items: baseline;
  gap: 8px;
}

.stat-number {
  font-size: 34px;
  font-weight: 1000;
  letter-spacing: -0.03em;
  color: var(--text);
  line-height: 1.05;
}

.stat-suffix {
  font-size: 14px;
  font-weight: 950;
  color: rgba(15, 23, 42, 0.75);
}

.stat-desc {
  margin: 10px 0 0;
  color: var(--muted);
  font-size: 13px;
  line-height: 1.35;
}

.stat-foot {
  margin-top: 12px;
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  align-items: center;
}

.stat-chip {
  display: inline-flex;
  padding: 7px 10px;
  border-radius: 999px;
  background: rgba(2, 6, 23, 0.03);
  border: 1px solid rgba(15, 23, 42, 0.10);
  font-weight: 950;
  font-size: 12px;
  color: rgba(15, 23, 42, 0.80);
}

.stat-note {
  font-size: 12px;
  font-weight: 850;
  color: rgba(100, 116, 139, 0.95);
}

/* Tabla comparativa */
.stats-table {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  overflow: hidden;
}

.stats-table-head {
  display: grid;
  grid-template-columns: 1fr 120px 120px 120px;
  gap: 10px;
  padding: 14px 16px;
  background: linear-gradient(135deg, rgba(177, 4, 14, 0.10), rgba(2, 6, 23, 0.02));
  border-bottom: 1px solid var(--line);
}

.th {
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 950;
  color: rgba(15, 23, 42, 0.78);
}
.th.right { text-align: right; }

.stats-table-body .tr {
  display: grid;
  grid-template-columns: 1fr 120px 120px 120px;
  gap: 10px;
  padding: 12px 16px;
  border-bottom: 1px solid rgba(15, 23, 42, 0.08);
}
.stats-table-body .tr:last-child { border-bottom: none; }

.td {
  color: rgba(15, 23, 42, 0.85);
  font-weight: 850;
  font-size: 13px;
}
.td.name { font-weight: 950; color: var(--text); }
.td.right { text-align: right; }

.var {
  display: inline-flex;
  justify-content: flex-end;
  width: 100%;
  font-weight: 950;
}
.var.up { color: rgba(15, 118, 110, 1); }
.var.down { color: rgba(185, 28, 28, 1); }

.stats-footnote {
  margin: 10px 16px 16px;
  color: rgba(100, 116, 139, 0.95);
  font-size: 12px;
}

/* Responsive */
@media (max-width: 991px) {
  .stats-hero { grid-template-columns: 1fr; }
  .stats-title { font-size: 28px; }
  .stats-grid { grid-template-columns: 1fr; }

  .stats-table-head,
  .stats-table-body .tr {
    grid-template-columns: 1fr;
  }
  .th.right, .td.right { text-align: left; }
  .var { justify-content: flex-start; }
}
</style>
