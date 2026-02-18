<template>
  <section :class="`brand-area ${spacing}`">
    <div :class="`container ${custom_container}`">
      <div class="row align-items-center">

        <!-- Left -->
        <div class="col-lg-4">
          <div class="tp-brand-2-content mb-40">
            <h4 class="tp-brand-2-title">
              ¿Por qué <br />
              estudiar con
              <span>
                nosotros?
                <img
                  class="tp-underline-shape-10 wow bounceIn"
                  data-wow-duration="1.5s"
                  data-wow-delay=".4s"
                  src="/images/unlerline/brand-2-svg-1.svg"
                  alt=""
                />
              </span>
            </h4>

            <p>
              Formación tecnológica pública con enfoque práctico,
              docentes comprometidos y oportunidades reales para tu futuro.
            </p>

            <div class="tp-brand-2-btn">
              <a class="tp-btn-round" href="/university-admission-overview">
                Conoce más
              </a>
            </div>
          </div>
        </div>

        <!-- Right -->
        <div class="col-lg-8">
          <div class="why-grid">
            <div v-for="(item, i) in why_items" :key="i" class="why-card">
              <div class="why-badge">{{ item.badge }}</div>
              <h5 class="why-title">{{ item.title }}</h5>
              <p class="why-text">{{ item.text }}</p>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
withDefaults(defineProps<{ custom_container?: string; spacing?: string }>(), {
  custom_container: '',
  spacing: 'mb-65'
});

const why_items = [
  {
    badge: "01",
    title: "Título Profesional Técnico",
    text: "Obtén una formación reconocida para insertarte al mercado laboral con seguridad."
  },
  {
    badge: "02",
    title: "Docentes Calificados",
    text: "Aprende con profesionales con experiencia y acompañamiento constante."
  },
  {
    badge: "03",
    title: "Laboratorios Modernos",
    text: "Fortalece tus competencias con prácticas en espacios equipados."
  },
  {
    badge: "04",
    title: "Bolsa de Trabajo",
    text: "Accede a oportunidades y convocatorias vinculadas a tu carrera."
  },
  {
    badge: "05",
    title: "Certificación Modular",
    text: "Avanza por módulos y certifica tu progreso durante la formación."
  },
  {
    badge: "06",
    title: "Experiencias Reales",
    text: "Proyectos, prácticas y actividades formativas conectadas con la realidad local."
  },
  {
    badge: "07",
    title: "Empleabilidad y Emprendimiento",
    text: "Desarrolla habilidades para trabajar o emprender con enfoque productivo."
  },
  {
    badge: "08",
    title: "Talleres Complementarios",
    text: "Refuerza tu perfil con Inglés e Informática para un mejor desempeño."
  }
];
</script>

<style scoped>
/* Grid moderno sin tocar el theme base */
.why-grid{
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 16px;
}

.why-card{
  background: #fff;
  border: 1px solid rgba(0,0,0,.06);
  border-radius: 14px;
  padding: 16px 16px 14px;
  transition: .2s ease;
}

.why-card:hover{
  transform: translateY(-2px);
  border-color: rgba(176,0,32,.35);
  box-shadow: 0 10px 24px rgba(0,0,0,.08);
}

.why-badge{
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 34px;
  height: 34px;
  border-radius: 10px;
  font-weight: 700;
  font-size: 13px;
  color: #b00020;
  background: rgba(176,0,32,.08);
  margin-bottom: 10px;
}

.why-title{
  margin: 0 0 6px;
  font-size: 16px;
  font-weight: 700;
  line-height: 1.2;
}

.why-text{
  margin: 0;
  font-size: 14px;
  opacity: .85;
  line-height: 1.35;
}

/* Responsive */
@media (max-width: 991px){
  .why-grid{
    grid-template-columns: 1fr;
  }
}
</style>
