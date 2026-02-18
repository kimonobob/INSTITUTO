<template>
  <section class="tp-course-details-area grey-bg pt-100 pb-120">
    <div class="container">
      <div class="row g-4">

        <!-- CONTENIDO -->
        <div class="col-lg-9">
          <div class="admi-wrap">

            <!-- Header (ROJO + TEXTO BLANCO) -->
            <div class="admi-hero admi-hero--red">
              <div class="admi-hero__badge">ADMISIÓN</div>
              <h2 class="admi-hero__title">Información General</h2>

              <p class="admi-hero__lead">
                El Instituto de Educación Superior Tecnológico Público realiza su proceso de admisión conforme a la
                normativa vigente del Ministerio de Educación, garantizando transparencia, igualdad de oportunidades y
                calidad en la formación profesional técnica.
              </p>

              <p class="admi-hero__lead">
                El proceso está dirigido a egresados de Educación Secundaria que deseen acceder a uno de nuestros
                programas de estudio y desarrollar una carrera profesional técnica orientada al desarrollo regional y
                nacional.
              </p>

              <div class="admi-hero__media">
                <img src="/images/course/details/course-details-thumb-1.jpg" alt="Admisión" />
              </div>
            </div>

            <!-- Cards -->
            <div class="admi-grid">

              <article class="admi-card">
                <div class="admi-card__icon" aria-hidden="true">
                  <!-- Target -->
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                    <path d="M12 21a9 9 0 1 0-9-9 9 9 0 0 0 9 9Z" stroke="currentColor" stroke-width="1.8" />
                    <path d="M12 17a5 5 0 1 0-5-5 5 5 0 0 0 5 5Z" stroke="currentColor" stroke-width="1.8" />
                    <path d="M12 13a1 1 0 1 0-1-1 1 1 0 0 0 1 1Z" fill="currentColor" />
                  </svg>
                </div>
                <div class="admi-card__body">
                  <h3 class="admi-card__title">Objetivo del Proceso</h3>
                  <p class="admi-card__text">
                    Seleccionar a los postulantes que demuestren las competencias básicas necesarias para iniciar
                    estudios superiores técnicos, asegurando un ingreso por orden de mérito y bajo criterios de
                    equidad.
                  </p>
                </div>
              </article>

              <article class="admi-card">
                <div class="admi-card__icon" aria-hidden="true">
                  <!-- Document -->
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                    <path
                      d="M8 3h7l3 3v15a2 2 0 0 1-2 2H8a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2Z"
                      stroke="currentColor" stroke-width="1.8" />
                    <path d="M15 3v3h3" stroke="currentColor" stroke-width="1.8" />
                    <path d="M9 11h6M9 15h6" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" />
                  </svg>
                </div>
                <div class="admi-card__body">
                  <h3 class="admi-card__title">Modalidades de Admisión</h3>
                  <ul class="admi-list">
                    <li><span class="admi-check">✓</span> Modalidad Ordinaria (Examen de admisión)</li>
                    <li><span class="admi-check">✓</span> Modalidad por Exoneración</li>
                    <li><span class="admi-check">✓</span> Traslado Externo</li>
                    <li><span class="admi-check">✓</span> Titulados o Graduados</li>
                  </ul>
                </div>
              </article>

              <article class="admi-card">
                <div class="admi-card__icon" aria-hidden="true">
                  <!-- Book -->
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                    <path
                      d="M4 5a2 2 0 0 1 2-2h10a2 2 0 0 1 2 2v15a2 2 0 0 0-2-2H6a2 2 0 0 0-2 2Z"
                      stroke="currentColor" stroke-width="1.8" />
                    <path d="M4 5v13" stroke="currentColor" stroke-width="1.8" />
                    <path d="M8 7h8M8 10h8" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" />
                  </svg>
                </div>
                <div class="admi-card__body">
                  <h3 class="admi-card__title">Evaluación</h3>
                  <p class="admi-card__text">La evaluación considera conocimientos y aptitudes en áreas como:</p>
                  <ul class="admi-list">
                    <li><span class="admi-check">✓</span> Comprensión lectora</li>
                    <li><span class="admi-check">✓</span> Razonamiento lógico-matemático</li>
                    <li><span class="admi-check">✓</span> Cultura general</li>
                  </ul>
                </div>
              </article>

              <article class="admi-card">
                <div class="admi-card__icon" aria-hidden="true">
                  <!-- Medal -->
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
                    <path d="M12 15a5 5 0 1 0-5-5 5 5 0 0 0 5 5Z" stroke="currentColor" stroke-width="1.8" />
                    <path d="M9 14 7 21l5-2 5 2-2-7" stroke="currentColor" stroke-width="1.8"
                      stroke-linejoin="round" />
                  </svg>
                </div>
                <div class="admi-card__body">
                  <h3 class="admi-card__title">Asignación de Vacantes</h3>
                  <p class="admi-card__text">
                    Las vacantes se adjudican en estricto orden de mérito, de acuerdo con el puntaje obtenido y el
                    número de plazas disponibles por programa de estudios.
                  </p>
                </div>
              </article>

            </div>
          </div>
        </div>

        <!-- SIDEBAR -->
        <div class="col-lg-3">
          <aside class="admi-side">
            <div class="admi-side__card">
              <h4 class="admi-side__title">Navegación</h4>
              <div class="admi-side__links">
                <nuxt-link href="/admission">Información General</nuxt-link>
                <nuxt-link href="/admission-proceso">Proceso de Admisión</nuxt-link>
                <nuxt-link href="/admission-tasas">Tasas Educativas</nuxt-link>
                <nuxt-link href="/admission-becas">Becas y Beneficios</nuxt-link>
                <nuxt-link href="/admission-cronograma">Cronograma</nuxt-link>
              </div>
            </div>

            <div class="admi-side__cta">
              <nuxt-link class="admi-cta-btn" href="/university-request-info">
                Solicitar Información
              </nuxt-link>
            </div>

            <div class="admi-side__card">
              <h4 class="admi-side__title">Contacto</h4>
              <p class="admi-side__text">Atención en oficina de admisión (horario institucional).</p>

              <a class="admi-side__contact" href="mailto:informes@instituto.edu.pe">
                <span>✉️</span> informes@instituto.edu.pe
              </a>

              <a class="admi-side__contact" href="tel:+51999999999">
                <span>📞</span> +51 999 999 999
              </a>
            </div>
          </aside>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts"></script>

<style scoped>
:root{
  --red: #c41230;
  --red2:#ff1e1e;
  --dark: #101114;
  --muted: #5f6673;
}

/* Wrapper */
.admi-wrap{
  display:flex;
  flex-direction: column;
  gap: 22px;
}

/* HERO BASE */
.admi-hero{
  border-radius: 22px;
  padding: 28px;
  box-shadow: 0 18px 60px rgba(16,17,20,0.10);
}

/* HERO ROJO + BLANCO */
.admi-hero--red{
  background: linear-gradient(135deg, #d41735, #a10f26);
  color: #ffffff;
  border: 0;
}


.admi-hero__badge{
  display:inline-block;
  font-size: 12px;
  font-weight: 900;
  letter-spacing: 1px;
  color: #fff;
  background: rgba(255,255,255,0.18);
  border: 0;
  padding: 8px 12px;
  border-radius: 999px;
  margin-bottom: 12px;
}

.admi-hero__title{
  font-size: 44px;
  font-weight: 950;
  letter-spacing: -1px;
  margin: 0 0 10px;
  color: #fff;
}

.admi-hero__lead{
  font-size: 17px;
  line-height: 1.9;
  margin: 0 0 10px;
  color: rgba(255,255,255,0.92);
}

.admi-hero__media{
  margin-top: 18px;
  border-radius: 18px;
  overflow:hidden;
  border: 0;
}
.admi-hero__media img{
  width:100%;
  height: 260px;
  object-fit: cover;
  display:block;
  filter: saturate(1.05) contrast(1.02);
}

/* GRID */
.admi-grid{
  display:grid;
  grid-template-columns: 1fr;
  gap: 16px;
}

/* CARD */
.admi-card{
  background:#fff;
  border-radius: 20px;
  padding: 20px;
  display:flex;
  gap: 14px;
  box-shadow: 0 14px 45px rgba(16,17,20,0.08);
  border: 0;
  position: relative;
  overflow:hidden;
  transition: transform .22s ease, box-shadow .22s ease;
  will-change: transform;
}
.admi-card:hover{
  transform: translateY(-4px) scale(1.01);
  box-shadow: 0 26px 80px rgba(196,18,48,0.18);
}

/* Barra roja */
.admi-card::before{
  content:"";
  position:absolute;
  left:0; top:0; bottom:0;
  width: 6px;
  background: linear-gradient(180deg, var(--red2), var(--red));
}

/* Icon */
.admi-card__icon{
  width: 46px;
  height: 46px;
  border-radius: 16px;
  display:flex;
  align-items:center;
  justify-content:center;
  background: linear-gradient(135deg, rgba(255,30,30,0.16), rgba(196,18,48,0.10));
  color: var(--red);
  margin-left: 8px;
  flex: 0 0 auto;
  border: 0;
}
.admi-card__icon svg{ display:block; }

/* Texts */
.admi-card__title{
  font-size: 18px;
  font-weight: 950;
  color: var(--dark);
  margin: 0 0 8px;
}
.admi-card__text{
  font-size: 16px;
  line-height: 1.9;
  color: var(--muted);
  margin: 0;
}

/* Lists */
.admi-list{
  padding-left: 0;
  margin: 10px 0 0;
  list-style: none;
  display:flex;
  flex-direction: column;
  gap: 10px;
}
.admi-list li{
  display:flex;
  gap: 10px;
  align-items:flex-start;
  color: var(--muted);
  font-size: 16px;
  line-height: 1.6;
}
.admi-check{
  width: 22px;
  height: 22px;
  border-radius: 7px;
  background: linear-gradient(135deg, var(--red2), var(--red));
  color:#fff;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size: 12px;
  font-weight: 900;
  flex: 0 0 auto;
  margin-top: 2px;
}

/* Sidebar */
.admi-side{
  position: sticky;
  top: 110px;
  display:flex;
  flex-direction: column;
  gap: 14px;
}

.admi-side__card{
  background:#fff;
  border-radius: 20px;
  padding: 18px;
  box-shadow: 0 14px 45px rgba(16,17,20,0.08);
  border: 0; /* sin borde */
}

.admi-side__title{
  font-size: 16px;
  font-weight: 950;
  color: var(--dark);
  margin: 0 0 10px;
}

/* NAV: más intensa, sin borde, más "botón" */
.admi-side__links{
  display:flex;
  flex-direction: column;
  gap: 10px;
}
.admi-side__links a{
  color: #fff;
  font-weight: 900;
  font-size: 14px;
  text-decoration: none;
  padding: 12px 14px;
  border-radius: 14px;
  background: linear-gradient(135deg, rgba(255,30,30,0.95), rgba(196,18,48,0.95));
  border: 0;
  transition: transform .2s ease, filter .2s ease;
  will-change: transform;
  box-shadow: 0 12px 30px rgba(196,18,48,0.18);
}
.admi-side__links a:hover{
  transform: translateY(-2px) scale(1.01);
  filter: brightness(0.98);
}

/* CTA: arreglado para que se vea sí o sí */
.admi-cta-btn{
  display:flex;
  align-items:center;
  justify-content:center;
  width: 100%;
  height: 54px;
  border-radius: 16px;
  background: #101114;
  color: #fff;
  font-weight: 950;
  text-decoration: none;
  box-shadow: 0 18px 40px rgba(16,17,20,0.18);
  transition: transform .2s ease, filter .2s ease;
  will-change: transform;
}
.admi-cta-btn:hover{
  transform: translateY(-2px) scale(1.02);
  filter: brightness(1.05);
}

.admi-side__text{
  color: var(--muted);
  font-size: 14px;
  line-height: 1.7;
  margin: 0 0 10px;
}

.admi-side__contact{
  display:flex;
  gap: 10px;
  align-items:center;
  color: var(--dark);
  font-weight: 800;
  font-size: 14px;
  text-decoration:none;
  padding: 12px 14px;
  border-radius: 14px;
  background: rgba(16,17,20,0.04);
  border: 0;
  margin-top: 10px;
  transition: transform .2s ease, background .2s ease, color .2s ease;
  will-change: transform;
}
.admi-side__contact:hover{
  transform: translateY(-2px) scale(1.01);
  background: rgba(196,18,48,0.10);
  color: var(--red);
}

/* Responsive */
@media (max-width: 991px){
  .admi-side{ position: static; top: auto; }
  .admi-hero__title{ font-size: 34px; }
  .admi-hero__media img{ height: 220px; }
}
</style>
