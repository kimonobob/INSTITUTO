<template>
  <div>
    <nuxt-layout name="layout-eight">

      <breadcrumb-one
        title="Tasas Educativas"
        subtitle="Admisión"
        :admission="true"
      />

      <section class="tp-tution-area grey-bg pt-120 pb-120">
        <div class="container">
          <div class="row justify-content-center">
            <div class="col-lg-11">

              <!-- ============================= -->
              <!-- BLOQUE 1: INSCRIPCIÓN -->
              <!-- Imagen IZQUIERDA -->
              <!-- ============================= -->
              <div class="modern-split mb-120">

                <!-- Imagen -->
                <div class="image-card">
                  <img
                    src="/images/program/4/c2.png"
                    class="hero-img"
                    alt="Derecho de Inscripción"
                  />
                  <div class="image-overlay">
                    <span class="tag">Admisión 2024</span>
                    <h3>Derecho de Inscripción</h3>
                    <p>Montos por modalidad de postulación.</p>
                  </div>
                </div>

                <!-- Cuadro -->
                <div class="modern-box">
                  <h2 class="section-title">
                    Derecho de Inscripción – Proceso de Admisión 2024
                  </h2>

                  <div class="fee-table">
                    <div class="fee-row fee-head">
                      <div>Concepto</div>
                      <div>Monto</div>
                    </div>

                    <div
                      v-for="(item, index) in inscripcion"
                      :key="index"
                      class="fee-row"
                    >
                      <div>{{ item.concept }}</div>
                      <div>
                        <span class="amount-pill">
                          {{ item.amount }}
                        </span>
                      </div>
                    </div>
                  </div>
                </div>

              </div>

              <!-- ============================= -->
              <!-- BLOQUE 2: MATRÍCULA -->
              <!-- Imagen DERECHA -->
              <!-- ============================= -->
              <div class="modern-split reverse">

                <!-- Cuadro -->
                <div class="modern-box">
                  <h2 class="section-title">
                    Matrícula de Ingresantes 2024
                  </h2>

                  <div class="fee-table">
                    <div class="fee-row fee-head">
                      <div>Concepto</div>
                      <div>Monto</div>
                    </div>

                    <div
                      v-for="(item, index) in matricula"
                      :key="index"
                      class="fee-row"
                    >
                      <div>{{ item.concept }}</div>
                      <div>
                        <span class="amount-pill">
                          {{ item.amount }}
                        </span>
                      </div>
                    </div>
                  </div>
                </div>

                <!-- Imagen -->
                <div class="image-card">
                  <img
                    src="/images/program/4/i2.png"
                    class="hero-img"
                    alt="Matrícula de Ingresantes"
                  />
                  <div class="image-overlay">
                    <span class="tag">Ingresantes 2024</span>
                    <h3>Matrícula</h3>
                    <p>Costos aplicables a nuevos estudiantes.</p>
                  </div>
                </div>

              </div>

            </div>
          </div>
        </div>
      </section>

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
definePageMeta({ layout: false });

useSeoMeta({
  title: "Tasas Educativas - Admisión 2024",
});

const inscripcion = [
  { concept: "Postulante Ordinario", amount: "S/. 150" },
  { concept: "Profesional", amount: "S/. 180" },
  { concept: "Traslado Interno", amount: "S/. 160" },
  { concept: "Primer Puesto", amount: "S/. 170" },
  { concept: "Deportista Calificado", amount: "S/. 170" },
  { concept: "Discapacidad", amount: "S/. 170" },
  { concept: "Servicio Militar", amount: "S/. 170" },
  { concept: "PIR (Víctima del Terrorismo)", amount: "S/. 00" },
];

const matricula = [
  { concept: "Matrícula Ingresante", amount: "S/. 120" },
  { concept: "Matrícula Profesional", amount: "S/. 140" },
  { concept: "Traslado Interno", amount: "S/. 110" },
  { concept: "Traslado Externo", amount: "S/. 130" },
  { concept: "Modalidades Especiales", amount: "S/. 120" },
];
</script>

<style scoped>

/* Layout */
.modern-split {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.reverse {
  direction: rtl;
}

.reverse > * {
  direction: ltr;
}

/* Imagen */
.image-card {
  position: relative;
  min-height: 450px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 15px 40px rgba(0,0,0,0.08);
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.image-overlay {
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 25px;
  background: linear-gradient(to top, rgba(0,0,0,0.75), transparent);
  color: white;
}

.tag {
  font-size: 12px;
  background: rgba(255,255,255,0.2);
  padding: 6px 12px;
  border-radius: 50px;
  display: inline-block;
  margin-bottom: 10px;
}

/* Cuadro */
.modern-box {
  background: white;
  padding: 40px;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.05);
}

.section-title {
  font-weight: 800;
  margin-bottom: 25px;
}

/* Tabla */
.fee-table {
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  overflow: hidden;
}

.fee-row {
  display: grid;
  grid-template-columns: 1fr 140px;
  padding: 14px 20px;
  border-bottom: 1px solid #f1f5f9;
  align-items: center;
}

.fee-head {
  background: #f8fafc;
  font-weight: 700;
}

.fee-row:last-child {
  border-bottom: none;
}

.amount-pill {
  background: #111827;
  color: white;
  padding: 6px 14px;
  border-radius: 50px;
  font-weight: 700;
  font-size: 13px;
}

/* Responsive */
@media (max-width: 991px) {
  .modern-split {
    grid-template-columns: 1fr;
  }

  .reverse {
    direction: ltr;
  }

  .image-card {
    min-height: 280px;
  }

  .fee-row {
    grid-template-columns: 1fr;
  }

  .amount-pill {
    margin-top: 8px;
    display: inline-block;
  }
}

</style>
