<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-one title="Licenciamiento" subtitle="Transparencia" />
      <!-- breadcrumb area end -->

      <!-- Licenciamiento start -->
      <section class="lic-area grey-bg pt-110 pb-90">
        <div class="container">
          <div class="row align-items-stretch">

            <!-- Left: Hero / Status -->
            <div class="col-lg-7">
              <div class="lic-hero">
                <div class="lic-badge">
                  <span class="dot"></span>
                  Estado del licenciamiento
                </div>

                <h2 class="lic-title">
                  Licenciamiento Institucional
                  <span class="lic-underline"></span>
                </h2>

                <p class="lic-lead">
                  En esta sección publicamos información relacionada al licenciamiento, acciones de mejora y
                  evidencias institucionales, con enfoque en transparencia y calidad educativa.
                </p>

                <div class="lic-status-card">
                  <div class="lic-status-left">
                    <p class="lic-status-label">Situación actual</p>
                    <h3 class="lic-status-value">{{ statusLabel }}</h3>
                    <p class="lic-status-note">
                      * Texto referencial. Cuando tengas la resolución o el documento oficial, podrás actualizar esta sección.
                    </p>
                  </div>

                  <div class="lic-status-right">
                    <div class="lic-ring">
                      <svg viewBox="0 0 120 120" aria-hidden="true">
                        <circle cx="60" cy="60" r="46" class="ring-bg"></circle>
                        <circle
                          cx="60" cy="60" r="46"
                          class="ring"
                          :style="{ strokeDashoffset: ringOffset }"
                        ></circle>
                      </svg>
                      <div class="lic-ring-text">
                        <span class="lic-ring-num">{{ progress }}%</span>
                        <span class="lic-ring-sub">avance</span>
                      </div>
                    </div>

                    <div class="lic-cta">
                      <button class="lic-btn" type="button" @click="toggleDetails">
                        {{ showDetails ? "Ocultar detalle" : "Ver detalle" }}
                        <span aria-hidden="true">→</span>
                      </button>

                      <button class="lic-btn lic-btn--ghost" type="button" disabled aria-disabled="true">
                        Descargar resolución (próximamente)
                      </button>
                    </div>
                  </div>
                </div>

                <transition name="fade">
                  <div v-if="showDetails" class="lic-details">
                    <div class="lic-details-head">
                      <h4 class="lic-details-title">Componentes de licenciamiento</h4>

                      <div class="lic-filter">
                        <label for="filter">Filtrar</label>
                        <select id="filter" v-model="filter">
                          <option value="all">Todos</option>
                          <option value="academico">Académico</option>
                          <option value="gestion">Gestión</option>
                          <option value="infra">Infraestructura</option>
                          <option value="bienestar">Bienestar</option>
                        </select>
                      </div>
                    </div>

                    <div class="lic-steps">
                      <article
                        v-for="item in filteredItems"
                        :key="item.id"
                        class="lic-step"
                      >
                        <div class="step-top">
                          <span :class="['step-tag', item.category]">
                            {{ item.categoryLabel }}
                          </span>

                          <span class="step-progress">
                            {{ item.value }}%
                          </span>
                        </div>

                        <h5 class="step-title">{{ item.title }}</h5>
                        <p class="step-desc">{{ item.description }}</p>

                        <div class="step-bar" role="progressbar" :aria-valuenow="item.value" aria-valuemin="0" aria-valuemax="100">
                          <div class="step-bar-fill" :style="{ width: item.value + '%' }"></div>
                        </div>

                        <p class="step-foot">
                          Evidencias: <strong>{{ item.evidence }}</strong>
                        </p>
                      </article>
                    </div>
                  </div>
                </transition>

              </div>
            </div>

            <!-- Right: Timeline / Evidence -->
            <div class="col-lg-5">
              <div class="lic-panel">
                <div class="lic-panel-head">
                  <h3 class="lic-panel-title">Ruta de evidencias</h3>
                  <p class="lic-panel-sub">
                    Organiza publicaciones por etapas. Puedes actualizar años, hitos y archivos cuando los tengas.
                  </p>
                </div>

                <div class="lic-timeline">
                  <div v-for="t in timeline" :key="t.id" class="tl-item">
                    <div class="tl-left">
                      <span class="tl-year">{{ t.year }}</span>
                      <span class="tl-dot" aria-hidden="true"></span>
                      <span class="tl-line" aria-hidden="true"></span>
                    </div>

                    <div class="tl-right">
                      <h4 class="tl-title">{{ t.title }}</h4>
                      <p class="tl-desc">{{ t.description }}</p>

                      <div class="tl-actions">
                        <button
                          class="tl-btn"
                          type="button"
                          :disabled="!t.url"
                          :aria-disabled="!t.url"
                          :title="t.url ? 'Ver documento' : 'Próximamente'"
                          @click="openDoc(t.url)"
                        >
                          Ver documento
                        </button>

                        <button
                          class="tl-btn tl-btn--ghost"
                          type="button"
                          disabled
                          aria-disabled="true"
                        >
                          Descargar (próximamente)
                        </button>
                      </div>
                    </div>
                  </div>
                </div>

                <div class="lic-panel-foot">
                  <div class="foot-box">
                    <h5>¿Qué publicaremos aquí?</h5>
                    <ul>
                      <li>Resoluciones y comunicados oficiales</li>
                      <li>Planes de mejora y avances</li>
                      <li>Informes y evidencias institucionales</li>
                    </ul>
                  </div>

                  <div class="foot-alert">
                    <span class="alert-dot" aria-hidden="true"></span>
                    <p>
                      Cuando tengas los PDFs, solo agrega la propiedad <code>url</code> en el script y se habilitarán los botones.
                    </p>
                  </div>
                </div>

              </div>
            </div>

          </div>
        </div>
      </section>
      <!-- Licenciamiento end -->

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "Licenciamiento - IESTP" });

type LicItem = {
  id: number;
  category: "academico" | "gestion" | "infra" | "bienestar";
  categoryLabel: string;
  title: string;
  description: string;
  value: number; // 0-100
  evidence: string;
};

type TimelineItem = {
  id: number;
  year: string;
  title: string;
  description: string;
  url?: string; // futuro: PDF/enlace
};

const showDetails = ref(true);
const filter = ref<"all" | "academico" | "gestion" | "infra" | "bienestar">("all");

/**
 * ✅ Puedes ajustar estos textos a tu realidad.
 * La idea es que sea DIFERENTE a las otras pestañas: aquí hay "estado + progreso + timeline".
 */
const statusLabel = ref("En proceso de actualización");
const progress = computed(() => {
  const values = items.value.map((i) => i.value);
  const avg = values.reduce((a, b) => a + b, 0) / Math.max(1, values.length);
  return Math.round(avg);
});

// círculo progreso
const circumference = 2 * Math.PI * 46;
const ringOffset = computed(() => {
  const p = Math.min(100, Math.max(0, progress.value));
  return `${circumference - (circumference * p) / 100}`;
});

const items = ref<LicItem[]>([
  {
    id: 1,
    category: "academico",
    categoryLabel: "Académico",
    title: "Gestión académica y pertinencia",
    description:
      "Estructura curricular, sílabos y enfoque por competencias alineados a la formación técnica.",
    value: 78,
    evidence: "Currículos, sílabos, actas, planes de estudio",
  },
  {
    id: 2,
    category: "infra",
    categoryLabel: "Infraestructura",
    title: "Ambientes, laboratorios y equipamiento",
    description:
      "Mejoras y mantenimiento de infraestructura para asegurar condiciones adecuadas de aprendizaje.",
    value: 70,
    evidence: "Inventarios, fichas técnicas, mantenimiento, fotografías",
  },
  {
    id: 3,
    category: "gestion",
    categoryLabel: "Gestión",
    title: "Gestión institucional y transparencia",
    description:
      "Documentos de gestión, procesos internos y organización administrativa orientada a resultados.",
    value: 82,
    evidence: "PEI, PAT, RI, TUPA, informes",
  },
  {
    id: 4,
    category: "bienestar",
    categoryLabel: "Bienestar",
    title: "Bienestar estudiantil y empleabilidad",
    description:
      "Acompañamiento, tutoría, actividades y acciones de inserción laboral.",
    value: 74,
    evidence: "Registros de atención, convenios, reportes",
  },
]);

const filteredItems = computed(() => {
  if (filter.value === "all") return items.value;
  return items.value.filter((i) => i.category === filter.value);
});

const timeline = ref<TimelineItem[]>([
  {
    id: 1,
    year: "2023",
    title: "Diagnóstico y organización de evidencias",
    description:
      "Levantamiento de información, revisión documental y ordenamiento por componentes.",
  },
  {
    id: 2,
    year: "2024",
    title: "Plan de mejora y actualización normativa",
    description:
      "Acciones de mejora continua, fortalecimiento de procesos y actualización de instrumentos de gestión.",
  },
  {
    id: 3,
    year: "2025",
    title: "Consolidación y publicación de documentos",
    description:
      "Publicación progresiva de reportes, evidencias y documentos institucionales vinculados.",
  },
]);

function toggleDetails() {
  showDetails.value = !showDetails.value;
}

function openDoc(url?: string) {
  if (!url) return;
  window.open(url, "_blank", "noopener,noreferrer");
}
</script>

<style scoped>
/* ===== Licenciamiento - diseño único (diferente a las otras pestañas) ===== */
.lic-area {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* HERO */
.lic-hero {
  border-radius: 26px;
  border: 1px solid var(--line);
  background:
    radial-gradient(1100px 500px at 20% 0%, rgba(177, 4, 14, 0.14), transparent 55%),
    radial-gradient(900px 420px at 110% 10%, rgba(15, 23, 42, 0.08), transparent 60%),
    linear-gradient(180deg, rgba(255,255,255,0.92), rgba(255,255,255,0.76));
  box-shadow: 0 18px 70px rgba(2, 6, 23, 0.10);
  padding: 20px;
  position: relative;
  overflow: hidden;
  height: 100%;
}

.lic-badge {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 8px 12px;
  border-radius: 999px;
  border: 1px solid rgba(177, 4, 14, 0.22);
  background: rgba(177, 4, 14, 0.10);
  color: var(--brand);
  font-weight: 950;
  font-size: 12px;
  letter-spacing: 0.06em;
  text-transform: uppercase;
}

.lic-badge .dot {
  width: 10px;
  height: 10px;
  background: var(--brand);
  border-radius: 50%;
  box-shadow: 0 0 0 6px rgba(177, 4, 14, 0.12);
}

.lic-title {
  margin: 14px 0 8px;
  font-size: 40px;
  font-weight: 1000;
  letter-spacing: -0.04em;
  color: var(--text);
  line-height: 1.1;
  position: relative;
}

.lic-underline {
  display: block;
  width: 180px;
  height: 6px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--brand), var(--brand2));
  margin-top: 10px;
  opacity: 0.95;
}

.lic-lead {
  margin: 0 0 16px;
  color: rgba(100, 116, 139, 0.98);
  font-size: 15px;
  max-width: 70ch;
}

/* STATUS CARD */
.lic-status-card {
  display: grid;
  grid-template-columns: 1fr 280px;
  gap: 14px;
  border-radius: 22px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(255, 255, 255, 0.92);
  padding: 16px;
}

.lic-status-label {
  margin: 0;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-weight: 950;
  color: rgba(15, 23, 42, 0.70);
}

.lic-status-value {
  margin: 6px 0 6px;
  font-size: 24px;
  font-weight: 1000;
  letter-spacing: -0.02em;
  color: var(--text);
}

.lic-status-note {
  margin: 0;
  font-size: 12px;
  color: rgba(100, 116, 139, 0.95);
}

/* Ring */
.lic-ring {
  width: 150px;
  height: 150px;
  position: relative;
  margin-left: auto;
}

.lic-ring svg {
  width: 150px;
  height: 150px;
  transform: rotate(-90deg);
}

.ring-bg {
  fill: none;
  stroke: rgba(15, 23, 42, 0.10);
  stroke-width: 10;
}

.ring {
  fill: none;
  stroke: url(#grad);
  stroke: var(--brand);
  stroke-width: 10;
  stroke-linecap: round;
  stroke-dasharray: 289;
  transition: stroke-dashoffset 0.4s ease;
}

.lic-ring-text {
  position: absolute;
  inset: 0;
  display: grid;
  place-content: center;
  text-align: center;
}

.lic-ring-num {
  font-size: 30px;
  font-weight: 1000;
  color: var(--text);
  line-height: 1;
}

.lic-ring-sub {
  font-size: 12px;
  font-weight: 900;
  color: rgba(100, 116, 139, 0.95);
}

.lic-cta {
  display: grid;
  gap: 10px;
  margin-top: 12px;
}

.lic-btn {
  width: 100%;
  border: none;
  border-radius: 999px;
  padding: 11px 14px;
  font-weight: 950;
  font-size: 13px;
  color: #fff;
  background: linear-gradient(135deg, var(--brand), var(--brand2));
  border: 1px solid rgba(177, 4, 14, 0.35);
  box-shadow: 0 16px 40px rgba(177, 4, 14, 0.22);
  transition: transform 0.12s ease, box-shadow 0.12s ease;
}

.lic-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 20px 55px rgba(177, 4, 14, 0.26);
}

.lic-btn--ghost {
  background: rgba(2, 6, 23, 0.06);
  color: rgba(15, 23, 42, 0.65);
  border-color: rgba(2, 6, 23, 0.10);
  box-shadow: none;
  cursor: not-allowed;
}

/* DETAILS */
.lic-details {
  margin-top: 14px;
  border-radius: 22px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(255, 255, 255, 0.92);
  padding: 16px;
}

.lic-details-head {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 12px;
  margin-bottom: 12px;
}

.lic-details-title {
  margin: 0;
  font-size: 16px;
  font-weight: 1000;
  color: var(--text);
  letter-spacing: -0.02em;
}

.lic-filter label {
  display: block;
  font-size: 12px;
  font-weight: 900;
  color: rgba(15, 23, 42, 0.70);
  margin-bottom: 6px;
}

.lic-filter select {
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.14);
  background: rgba(255, 255, 255, 0.96);
  padding: 10px 12px;
  font-weight: 900;
  color: var(--text);
  outline: none;
}

.lic-steps {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 12px;
}

.lic-step {
  border-radius: 18px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(2, 6, 23, 0.02);
  padding: 12px;
}

.step-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  margin-bottom: 8px;
}

.step-tag {
  font-size: 11px;
  font-weight: 950;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  padding: 6px 10px;
  border-radius: 999px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(255,255,255,0.85);
}

.step-tag.academico { color: rgba(15, 23, 42, 0.85); }
.step-tag.gestion { color: rgba(15, 23, 42, 0.85); }
.step-tag.infra { color: rgba(15, 23, 42, 0.85); }
.step-tag.bienestar { color: rgba(15, 23, 42, 0.85); }

.step-progress {
  font-weight: 1000;
  color: var(--text);
}

.step-title {
  margin: 0 0 6px;
  font-size: 14px;
  font-weight: 1000;
  color: var(--text);
}

.step-desc {
  margin: 0 0 10px;
  font-size: 13px;
  color: rgba(100, 116, 139, 0.98);
  line-height: 1.35;
}

.step-bar {
  width: 100%;
  height: 10px;
  border-radius: 999px;
  background: rgba(15, 23, 42, 0.10);
  overflow: hidden;
}

.step-bar-fill {
  height: 100%;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--brand), var(--brand2));
}

.step-foot {
  margin: 10px 0 0;
  font-size: 12px;
  color: rgba(100, 116, 139, 0.98);
}

/* RIGHT PANEL */
.lic-panel {
  height: 100%;
  border-radius: 26px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.92);
  box-shadow: 0 18px 70px rgba(2, 6, 23, 0.10);
  overflow: hidden;
}

.lic-panel-head {
  padding: 18px;
  background:
    radial-gradient(900px 350px at 20% 0%, rgba(177, 4, 14, 0.10), transparent 55%),
    linear-gradient(135deg, rgba(2, 6, 23, 0.02), rgba(255, 255, 255, 0.92));
  border-bottom: 1px solid rgba(15, 23, 42, 0.10);
}

.lic-panel-title {
  margin: 0 0 8px;
  font-size: 18px;
  font-weight: 1000;
  color: var(--text);
  letter-spacing: -0.02em;
}

.lic-panel-sub {
  margin: 0;
  font-size: 13px;
  color: rgba(100, 116, 139, 0.98);
}

/* Timeline */
.lic-timeline {
  padding: 16px 18px 10px;
}

.tl-item {
  display: grid;
  grid-template-columns: 56px 1fr;
  gap: 12px;
  padding: 10px 0;
  position: relative;
}

.tl-left {
  position: relative;
  display: grid;
  justify-items: center;
  align-content: start;
}

.tl-year {
  font-size: 12px;
  font-weight: 1000;
  color: rgba(15, 23, 42, 0.75);
  padding: 6px 10px;
  border-radius: 999px;
  background: rgba(2, 6, 23, 0.04);
  border: 1px solid rgba(15, 23, 42, 0.10);
}

.tl-dot {
  width: 12px;
  height: 12px;
  background: var(--brand);
  border-radius: 50%;
  margin-top: 10px;
  box-shadow: 0 0 0 6px rgba(177, 4, 14, 0.12);
}

.tl-line {
  width: 2px;
  height: calc(100% - 40px);
  background: rgba(15, 23, 42, 0.10);
  margin-top: 10px;
}

.tl-title {
  margin: 0 0 6px;
  font-size: 14px;
  font-weight: 1000;
  color: var(--text);
}

.tl-desc {
  margin: 0 0 10px;
  font-size: 13px;
  color: rgba(100, 116, 139, 0.98);
  line-height: 1.35;
}

.tl-actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.tl-btn {
  border: none;
  border-radius: 999px;
  padding: 9px 12px;
  font-weight: 950;
  font-size: 12px;
  background: rgba(2, 6, 23, 0.06);
  color: rgba(15, 23, 42, 0.75);
  border: 1px solid rgba(2, 6, 23, 0.10);
}

.tl-btn:disabled {
  cursor: not-allowed;
  opacity: 0.7;
}

.tl-btn--ghost {
  opacity: 0.65;
}

/* Panel foot */
.lic-panel-foot {
  padding: 14px 18px 18px;
  border-top: 1px solid rgba(15, 23, 42, 0.10);
}

.foot-box h5 {
  margin: 0 0 8px;
  font-size: 13px;
  font-weight: 1000;
  color: var(--text);
}

.foot-box ul {
  margin: 0;
  padding-left: 18px;
  color: rgba(100, 116, 139, 0.98);
  font-size: 12px;
  line-height: 1.6;
}

.foot-alert {
  margin-top: 12px;
  display: grid;
  grid-template-columns: 18px 1fr;
  gap: 10px;
  align-items: start;
  padding: 12px;
  border-radius: 18px;
  border: 1px solid rgba(177, 4, 14, 0.18);
  background: rgba(177, 4, 14, 0.08);
}

.alert-dot {
  width: 12px;
  height: 12px;
  background: var(--brand);
  border-radius: 50%;
  margin-top: 4px;
}

.foot-alert p {
  margin: 0;
  font-size: 12px;
  color: rgba(15, 23, 42, 0.78);
}

.foot-alert code {
  background: rgba(255,255,255,0.85);
  border: 1px solid rgba(15, 23, 42, 0.10);
  padding: 1px 6px;
  border-radius: 8px;
  font-weight: 900;
}

/* Transitions */
.fade-enter-active, .fade-leave-active { transition: opacity 0.18s ease; }
.fade-enter-from, .fade-leave-to { opacity: 0; }

/* Responsive */
@media (max-width: 991px) {
  .lic-title { font-size: 30px; }
  .lic-status-card { grid-template-columns: 1fr; }
  .lic-ring { margin-left: 0; }
  .lic-steps { grid-template-columns: 1fr; }
}
</style>
