<template>
  <section id="down" class="institute-counter-area py-5 position-relative">
    <div class="grid-overlay"></div>

    <div class="container position-relative z-2 py-4">
      <div class="text-center mb-5 wow fadeInUp" data-wow-delay=".2s">
        <h2 class="text-white fw-bold mb-3 section-title">
          EL IESTP AYAVIRI EN CIFRAS
        </h2>
        <p class="text-light-red fs-5">
          Indicadores institucionales que reflejan nuestro compromiso académico
        </p>
      </div>

      <div class="row g-4 justify-content-center">
        <div 
          v-for="(counter, index) in counterData" 
          :key="counter.id" 
          class="col-lg-3 col-md-6 wow fadeInUp" 
          :data-wow-delay="`.${3 + index}s`"
        >
          <div class="counter-card text-center p-4 p-lg-5 h-100 d-flex flex-column justify-content-center">
            <p class="counter-label mb-2">{{ counter.title }}</p>
            <h3 class="counter-number mb-0">
              <counter-item :min="0" :max="counter.endValue" />
              <span v-if="counter.suffix">{{ counter.suffix }}</span>
            </h3>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Datos adaptados para el IESTP Ayaviri
const counterData = [
  {
    id: 1,
    endValue: 1986, // Cambia esto por el año real de fundación
    title: "Fundado en",
  },
  {
    id: 2,
    endValue: 6, // Cambia esto por el número real de programas
    title: "Programas de Estudio",
  },
  {
    id: 3,
    endValue: 45, // Número de docentes
    title: "Docentes Especializados",
  },
  {
    id: 4,
    endValue: 850, // Número de estudiantes
    title: "Estudiantes Matriculados",
    suffix: "+" 
  },
];
</script>

<style scoped>
/* Fondo principal rojo vino oscuro */
.institute-counter-area {
  background-color: #881337; /* Rojo institucional profundo */
  overflow: hidden;
}

/* Título con fuente serifa elegante */
.section-title {
  font-family: "Georgia", serif;
  font-size: 2.5rem;
  letter-spacing: 0.5px;
}

/* Subtítulo en un tono rosado/rojo muy claro para contrastar */
.text-light-red {
  color: #fecdd3;
}

/* Cuadrícula de fondo sutil */
.grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.06) 1px, transparent 1px);
  background-size: 40px 40px;
  z-index: 1;
}

/* Tarjetas de los contadores */
.counter-card {
  background-color: #9f1239; /* Un rojo un poco más claro que el fondo para que resalte */
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.08);
}

.counter-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
  background-color: #be123c; /* Se ilumina un poco más al pasar el mouse */
}

/* Textos de las tarjetas */
.counter-label {
  color: #f8fafc;
  font-size: 1.05rem;
  font-weight: 500;
}

/* Números en dorado cálido (combina perfecto con el rojo vino) */
.counter-number {
  color: #fbbf24; /* Dorado */
  font-size: 3rem;
  font-weight: 700;
  font-family: "Georgia", serif;
}

/* Para asegurar que tu componente <counter-item> herede el color dorado */
.counter-number :deep(*) {
  color: #fbbf24 !important;
}
</style>