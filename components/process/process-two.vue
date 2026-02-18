<template>
  <section class="tp-apply-process-area pb-60 apx-section">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-10">
          <div id="down" class="apx">
            <!-- Header -->
            <div class="apx__head text-center">
              <span class="apx__badge">ADMISIÓN</span>
              <h3 class="apx__title">Etapas del Proceso</h3>
              <p class="apx__subtitle">
                Sigue estos pasos en orden. La evaluación y asignación de vacantes se realiza por
                <strong>orden de mérito</strong>.
              </p>
            </div>

            <!-- Timeline -->
            <div class="apx__timeline">
              <article
                v-for="(step, index) in applicationProcess"
                :key="index"
                class="apx-card"
              >
                <!-- Left rail -->
                <div class="apx-card__rail">
                  <div class="apx-card__dot"></div>
                  <div class="apx-card__line" v-if="index !== applicationProcess.length - 1"></div>
                </div>

                <!-- Card -->
                <div class="apx-card__box">
                  <div class="apx-card__top">
                    <div class="apx-card__num">
                      <span class="apx-card__num-label">PASO</span>
                      <span class="apx-card__num-value">{{ step.step }}</span>
                    </div>

                    <div class="apx-card__meta">
                      <h4 class="apx-card__title">{{ step.title }}</h4>
                      <p class="apx-card__desc" v-html="step.description"></p>

                      <div class="apx-card__actions" v-if="step.linkText && step.linkHref">
                        <NuxtLink :to="step.linkHref" class="apx-btn">
                          {{ step.linkText }}
                          <span class="apx-btn__icon" aria-hidden="true">
                            <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                              <path d="M5 12h12" stroke="currentColor" stroke-width="2" stroke-linecap="round" />
                              <path
                                d="M13 6l6 6-6 6"
                                stroke="currentColor"
                                stroke-width="2"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                              />
                            </svg>
                          </span>
                        </NuxtLink>
                      </div>
                    </div>

                    <div class="apx-card__watermark" aria-hidden="true">
                      {{ step.step < 10 ? `0${step.step}` : step.step }}
                    </div>
                  </div>

                  <!-- Micro footer -->
                  <div class="apx-card__foot">
                    <span class="apx-pill">Etapa {{ step.step }}</span>
                    <span class="apx-pill apx-pill--dark">Proceso Institucional</span>
                  </div>
                </div>
              </article>
            </div>

            <!-- Note -->
            <div class="apx__note">
              <div class="apx__note-icon" aria-hidden="true">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none">
                  <path
                    d="M12 22a10 10 0 1 0-10-10 10 10 0 0 0 10 10Z"
                    stroke="currentColor"
                    stroke-width="1.8"
                  />
                  <path d="M12 8v5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" />
                  <path d="M12 16h.01" stroke="currentColor" stroke-width="2.6" stroke-linecap="round" />
                </svg>
              </div>
              <p class="apx__note-text">
                Los plazos, requisitos y vacantes se establecen en la convocatoria oficial vigente del instituto.
              </p>
            </div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";

type AdmissionStep = {
  step: number;
  title: string;
  description: string;
  linkText?: string;
  linkHref?: string;
};

const applicationProcess = ref<AdmissionStep[]>([
  {
    step: 1,
    title: "Convocatoria e Inscripción",
    description:
      "Revisa la convocatoria oficial, completa tu inscripción y presenta la documentación requerida dentro del plazo establecido.",
    linkText: "Solicitar Información",
    linkHref: "/university-request-info",
  },
  {
    step: 2,
    title: "Revisión de Expediente",
    description:
      "La institución verifica el cumplimiento de requisitos y la validez de la documentación presentada según lo establecido en la convocatoria.",
  },
  {
    step: 3,
    title: "Evaluación de Admisión",
    description:
      "Rinde la evaluación orientada a medir competencias básicas: comprensión lectora, razonamiento lógico-matemático y cultura general.",
  },
  {
    step: 4,
    title: "Publicación de Resultados",
    description:
      "Los resultados se publican en los canales oficiales. La asignación de vacantes se realiza por <strong>estricto orden de mérito</strong>.",
  },
  {
    step: 5,
    title: "Matrícula de Ingresantes",
    description:
      "Si obtienes vacante, formaliza tu ingreso mediante la matrícula dentro de los plazos establecidos.",
  },
]);
</script>

<style scoped>
/* ===== Paleta brutal (como antes) ===== */
:root{
  --apx-red: #c41230;
  --apx-red2:#ff1e1e;
  --apx-dark:#101114;
  --apx-white:#ffffff;
}

/* Fondo general BLANCO (aunque la sección tenga grey-bg) */
.apx-section{
  background: #ffffff !important;
}

/* Header */
.apx__head{ margin-bottom: 26px; }

.apx__badge{
  display:inline-flex;
  align-items:center;
  padding: 10px 14px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--apx-red2), var(--apx-red));
  color: var(--apx-white);
  font-weight: 950;
  letter-spacing: 1px;
  font-size: 12px;
  box-shadow: 0 18px 40px rgba(196,18,48,.25);
}

.apx__title{
  margin: 14px 0 10px;
  font-weight: 950;
  letter-spacing: -1px;
  font-size: 44px;
  color: var(--apx-dark);
}

.apx__subtitle{
  margin: 0 auto;
  max-width: 720px;
  color: rgba(16,17,20,.75);
  font-size: 16px;
  line-height: 1.9;
}

/* Timeline container */
.apx__timeline{
  display:flex;
  flex-direction: column;
  gap: 16px;
}

/* Card layout */
.apx-card{
  display:flex;
  gap: 14px;
}

/* Rail */
.apx-card__rail{
  width: 26px;
  display:flex;
  align-items:flex-start;
  flex-direction: column;
  padding-top: 18px;
}

.apx-card__dot{
  width: 14px;
  height: 14px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--apx-red2), var(--apx-red));
  box-shadow: 0 14px 32px rgba(196,18,48,.35);
  margin-left: 6px;
}

.apx-card__line{
  width: 2px;
  flex: 1;
  margin: 10px 0 0 12px;
  background: linear-gradient(180deg, rgba(196,18,48,.65), rgba(196,18,48,0));
}

/* ===== CARD ROJA + TEXTO BLANCO ===== */
.apx-card__box{
  position: relative;
  flex: 1;
  border-radius: 22px;
  overflow:hidden;
  border: 0;
  background: linear-gradient(135deg, var(--apx-red2), var(--apx-red));
  box-shadow: 0 22px 70px rgba(196,18,48,.22);
  transition: transform .22s ease, box-shadow .22s ease;
  will-change: transform;
}

.apx-card__box:hover{
  transform: translateY(-4px);
  box-shadow: 0 34px 110px rgba(196,18,48,.30);
}

/* Brillo sutil arriba */
.apx-card__box::after{
  content:"";
  position:absolute;
  inset: 0;
  background:
    radial-gradient(800px 240px at 20% 0%, rgba(255,255,255,.20), transparent 60%),
    radial-gradient(700px 220px at 100% 30%, rgba(0,0,0,.12), transparent 55%);
  pointer-events:none;
}

/* Top block */
.apx-card__top{
  position: relative;
  padding: 20px 20px 14px 22px;
  display:flex;
  gap: 16px;
  z-index: 1;
}

/* Number box (blanco translúcido) */
.apx-card__num{
  width: 92px;
  min-width: 92px;
  height: 92px;
  border-radius: 20px;
  background: rgba(255,255,255,.14);
  border: 1px solid rgba(255,255,255,.20);
  backdrop-filter: blur(6px);
  display:flex;
  flex-direction: column;
  align-items:center;
  justify-content:center;
  color: var(--apx-white);
}

.apx-card__num-label{
  font-size: 11px;
  font-weight: 950;
  letter-spacing: 1px;
  color: rgba(255,255,255,.85);
}

.apx-card__num-value{
  font-size: 34px;
  font-weight: 950;
  color: #fff;
  line-height: 1;
  margin-top: 3px;
}

/* Text */
.apx-card__meta{
  flex: 1;
  padding-right: 48px;
}

.apx-card__title{
  margin: 2px 0 8px;
  font-size: 20px;
  font-weight: 950;
  color: #fff;
}

.apx-card__desc{
  margin: 0;
  font-size: 16px;
  line-height: 1.85;
  color: rgba(255,255,255,.92);
}

/* CTA Button (NEGRO elegante para contraste) */
.apx-card__actions{
  margin-top: 14px;
}

.apx-btn{
  display:inline-flex;
  align-items:center;
  justify-content:center;
  gap: 10px;
  height: 48px;
  padding: 0 16px;
  border-radius: 14px;
  text-decoration:none;
  color:#fff;
  font-weight: 950;
  background: rgba(16,17,20,.92);
  border: 1px solid rgba(255,255,255,.18);
  box-shadow: 0 18px 45px rgba(0,0,0,.20);
  transition: transform .2s ease, filter .2s ease;
  will-change: transform;
}

.apx-btn:hover{
  transform: translateY(-2px) scale(1.02);
  filter: brightness(1.06);
}

.apx-btn__icon{ display:inline-flex; }

/* Watermark (blanco translúcido) */
.apx-card__watermark{
  position:absolute;
  right: 12px;
  top: 10px;
  font-size: 72px;
  font-weight: 950;
  color: rgba(255,255,255,0.18);
  pointer-events:none;
  line-height: 1;
  z-index: 1;
}

/* Foot pills */
.apx-card__foot{
  display:flex;
  gap: 10px;
  padding: 0 20px 18px 22px;
  z-index: 1;
  position: relative;
}

.apx-pill{
  display:inline-flex;
  align-items:center;
  justify-content:center;
  height: 34px;
  padding: 0 12px;
  border-radius: 999px;
  font-size: 12px;
  font-weight: 900;
  color: #fff;
  background: rgba(255,255,255,0.14);
  border: 1px solid rgba(255,255,255,0.18);
  backdrop-filter: blur(6px);
}

.apx-pill--dark{
  color: #fff;
  background: rgba(16,17,20,.28);
  border: 1px solid rgba(255,255,255,0.16);
}

/* Note (negro suave para contraste) */
.apx__note{
  margin-top: 18px;
  background: #101114;
  border-radius: 20px;
  padding: 16px 18px;
  display:flex;
  gap: 12px;
  align-items:flex-start;
  box-shadow: 0 18px 55px rgba(0,0,0,0.18);
}

.apx__note-icon{
  width: 40px;
  height: 40px;
  border-radius: 14px;
  display:flex;
  align-items:center;
  justify-content:center;
  background: rgba(255,255,255,0.10);
  color: #fff;
}

.apx__note-text{
  margin: 2px 0 0;
  color: rgba(255,255,255,0.88);
  font-size: 14px;
  line-height: 1.7;
}

/* Responsive */
@media (max-width: 991px){
  .apx__title{ font-size: 34px; }
  .apx-card__top{ flex-direction: column; }
  .apx-card__meta{ padding-right: 0; }
  .apx-card__num{
    width: 100%;
    min-width: 0;
    height: 76px;
    flex-direction: row;
    gap: 10px;
  }
  .apx-card__watermark{ font-size: 56px; }
}
.apx-card__box{
  background: linear-gradient(135deg, #ff1e1e, #c41230) !important;
  color: #ffffff;
}

</style>
