<template>
  <section class="scholarships-section grey-bg pb-110 pt-110">
    <div class="container">
      <div class="row align-items-center g-4">

        <!-- Left: Imagen / Banner -->
        <div class="col-lg-5">
          <div class="scholarships-media">
            <img
              class="scholarships-img"
              src="/images/program/4/c2.png"
              alt="Becas y beneficios"
            />

            <div class="scholarships-badge">
              <span class="badge-chip">Becas</span>
              <h3 class="badge-title">Apoyo para que sigas estudiando</h3>
              <p class="badge-text">
                Programas de becas y beneficios según disponibilidad y requisitos.
              </p>
            </div>
          </div>
        </div>

        <!-- Right: Contenido -->
        <div class="col-lg-7">
          <div class="scholarships-content">

            <div class="section-head">
              <span class="kicker">Beneficios estudiantiles</span>
              <h2 class="section-title">Becas y Apoyos</h2>
              <p class="section-subtitle">
                Conoce las opciones de apoyo económico y facilidades disponibles para nuestros estudiantes.
              </p>
            </div>

            <!-- Cards -->
            <div class="scholarships-grid">
              <article
                v-for="item in scholarships"
                :key="item.id"
                class="scholarship-card"
              >
                <div class="card-icon" v-html="item.icon" aria-hidden="true"></div>

                <div class="card-body">
                  <div class="card-top">
                    <span class="card-chip">{{ item.tag }}</span>
                  </div>

                  <h3 class="card-title">{{ item.title }}</h3>
                  <p class="card-text">{{ item.description }}</p>

                  <ul class="card-list">
                    <li v-for="(b, idx) in item.bullets" :key="idx">
                      <span class="dot" aria-hidden="true"></span>
                      <span>{{ b }}</span>
                    </li>
                  </ul>
                </div>
              </article>
            </div>

            <!-- CTA -->
            <div class="scholarships-cta">
              <div class="cta-left">
                <h4 class="cta-title">¿Deseas postular a una beca?</h4>
                <p class="cta-text">
                  Revisa requisitos, fechas y documentación en el área de Bienestar Estudiantil.
                </p>
              </div>

              <div class="cta-right">
                <a href="/admisión" class="cta-btn">
                  Ver requisitos
                  <span class="cta-arrow" aria-hidden="true">→</span>
                </a>
                <a href="/contacto" class="cta-link">Consultar</a>
              </div>
            </div>

            <!-- Nota -->
            <p class="fineprint">
              * La disponibilidad, cobertura y cronograma pueden variar según convocatoria y normativa vigente.
            </p>

          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
type Scholarship = {
  id: number;
  title: string;
  tag: string;
  description: string;
  bullets: string[];
  icon: string;
};

const scholarships: Scholarship[] = [
  {
    id: 1,
    tag: "Alto rendimiento",
    title: "Beca por Mérito Académico",
    description:
      "Reconoce el desempeño sobresaliente durante el periodo académico, promoviendo la excelencia y la continuidad de estudios.",
    bullets: ["Promedio destacado", "Constancia de matrícula", "Evaluación por convocatoria"],
    icon: `
      <svg width="26" height="26" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 2l2.2 6.7H21l-5.4 3.9 2.1 6.6L12 15.7 6.3 19.2l2.1-6.6L3 8.7h6.8L12 2Z"
          stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
      </svg>
    `,
  },
  {
    id: 2,
    tag: "Situación socioeconómica",
    title: "Beca de Apoyo Económico",
    description:
      "Brinda facilidades para estudiantes que requieren apoyo, priorizando casos debidamente sustentados según evaluación.",
    bullets: ["Ficha socioeconómica", "Sustento documentario", "Entrevista/validación"],
    icon: `
      <svg width="26" height="26" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 21s-7-4.4-7-10a4 4 0 0 1 7-2.3A4 4 0 0 1 19 11c0 5.6-7 10-7 10Z"
          stroke="currentColor" stroke-width="1.8" stroke-linejoin="round"/>
      </svg>
    `,
  },
  {
    id: 3,
    tag: "Modalidades especiales",
    title: "Beneficios y Exoneraciones",
    description:
      "Aplica a modalidades específicas (según norma interna), facilitando el acceso y la permanencia en la formación profesional.",
    bullets: ["Discapacidad / servicio militar", "Deportista calificado", "Evaluación por normativa"],
    icon: `
      <svg width="26" height="26" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M20 6l-11 11-5-5" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    `,
  },
];
</script>

<style scoped>
/* ===== Scholarships Modern UI ===== */
.scholarships-section {
  position: relative;
}

.scholarships-content {
  --brand: #b1040e;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

.section-head {
  margin-bottom: 18px;
  padding: 18px;
  background: linear-gradient(180deg, rgba(255,255,255,0.92), rgba(255,255,255,0.70));
  border: 1px solid var(--line);
  border-radius: 18px;
  box-shadow: 0 10px 30px rgba(2, 6, 23, 0.06);
}

.kicker {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  font-size: 12px;
  font-weight: 800;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--brand);
}

.section-title {
  margin: 8px 0 6px;
  font-size: 30px;
  line-height: 1.15;
  letter-spacing: -0.02em;
  color: var(--text);
  font-weight: 900;
}

.section-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
}

/* Left media */
.scholarships-media {
  position: relative;
  border-radius: 22px;
  overflow: hidden;
  border: 1px solid var(--line);
  box-shadow: 0 16px 45px rgba(2, 6, 23, 0.10);
  min-height: 520px;
  background: #fff;
}

.scholarships-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transform: scale(1.02);
}

.scholarships-badge {
  position: absolute;
  inset: auto 16px 16px 16px;
  border-radius: 18px;
  padding: 16px;
  color: #fff;
  background: linear-gradient(180deg, rgba(2,6,23,0.10), rgba(2,6,23,0.78));
  border: 1px solid rgba(255,255,255,0.16);
  backdrop-filter: blur(10px);
}

.badge-chip {
  display: inline-flex;
  padding: 6px 10px;
  border-radius: 999px;
  border: 1px solid rgba(255,255,255,0.25);
  background: rgba(255,255,255,0.10);
  font-size: 12px;
  font-weight: 700;
}

.badge-title {
  margin: 10px 0 6px;
  font-size: 18px;
  font-weight: 900;
  letter-spacing: -0.02em;
}

.badge-text {
  margin: 0;
  font-size: 13px;
  opacity: 0.92;
}

/* Cards grid */
.scholarships-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 14px;
  margin-top: 14px;
}

.scholarship-card {
  display: grid;
  grid-template-columns: 48px 1fr;
  gap: 14px;
  padding: 16px;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.95);
  border: 1px solid var(--line);
  box-shadow: 0 12px 30px rgba(2, 6, 23, 0.06);
  transition: transform 0.15s ease, box-shadow 0.15s ease, border-color 0.15s ease;
}

.scholarship-card:hover {
  transform: translateY(-2px);
  border-color: rgba(177, 4, 14, 0.25);
  box-shadow: 0 18px 45px rgba(2, 6, 23, 0.10);
}

.card-icon {
  width: 48px;
  height: 48px;
  border-radius: 16px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--soft);
  color: var(--brand);
  border: 1px solid rgba(177, 4, 14, 0.15);
}

.card-top {
  display: flex;
  justify-content: flex-start;
  margin-bottom: 8px;
}

.card-chip {
  display: inline-flex;
  padding: 6px 10px;
  border-radius: 999px;
  background: rgba(2, 6, 23, 0.04);
  border: 1px solid rgba(2, 6, 23, 0.10);
  color: var(--text);
  font-size: 12px;
  font-weight: 800;
}

.card-title {
  margin: 0 0 6px;
  font-size: 16px;
  font-weight: 900;
  color: var(--text);
  letter-spacing: -0.01em;
}

.card-text {
  margin: 0 0 10px;
  color: var(--muted);
  font-size: 13px;
  line-height: 1.45;
}

.card-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  gap: 8px;
}

.card-list li {
  display: grid;
  grid-template-columns: 10px 1fr;
  gap: 10px;
  align-items: start;
  color: var(--text);
  font-size: 13px;
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 999px;
  background: rgba(177, 4, 14, 0.75);
  margin-top: 6px;
}

/* CTA */
.scholarships-cta {
  margin-top: 14px;
  border-radius: 18px;
  border: 1px solid var(--line);
  background: linear-gradient(180deg, rgba(255,255,255,0.92), rgba(255,255,255,0.75));
  box-shadow: 0 12px 30px rgba(2, 6, 23, 0.06);
  padding: 16px;
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 14px;
  align-items: center;
}

.cta-title {
  margin: 0 0 6px;
  font-size: 16px;
  font-weight: 900;
  color: var(--text);
}

.cta-text {
  margin: 0;
  color: var(--muted);
  font-size: 13px;
}

.cta-right {
  display: inline-flex;
  gap: 12px;
  align-items: center;
}

.cta-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 14px;
  border-radius: 999px;
  background: var(--brand);
  color: #fff;
  font-weight: 900;
  font-size: 13px;
  border: 1px solid rgba(177, 4, 14, 0.35);
  text-decoration: none;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.cta-btn:hover {
  transform: translateY(-1px);
  box-shadow: 0 14px 30px rgba(177, 4, 14, 0.20);
}

.cta-link {
  color: var(--text);
  font-weight: 800;
  text-decoration: none;
  border-bottom: 1px solid rgba(15, 23, 42, 0.20);
}

.cta-link:hover {
  border-bottom-color: rgba(177, 4, 14, 0.45);
}

.fineprint {
  margin: 12px 2px 0;
  color: rgba(100, 116, 139, 0.95);
  font-size: 12px;
}

/* Responsive */
@media (max-width: 991px) {
  .scholarships-media {
    min-height: 320px;
  }
  .scholarships-grid {
    grid-template-columns: 1fr;
  }
  .scholarships-cta {
    grid-template-columns: 1fr;
  }
}
</style>
