<template>
  <section class="faq-modern-area py-5 bg-light-gray">
    <div class="container">
      <div class="row justify-content-center mb-5">
        <div class="col-lg-8 text-center">
          <h2 class="section-title fw-bold text-dark-blue mb-3">Preguntas Frecuentes</h2>
          <p class="text-muted fs-5">Resuelve tus dudas sobre el proceso de admisión, requisitos y programas de estudio.</p>
        </div>
      </div>

      <div class="row g-5">
        <div class="col-lg-4">
          <div class="faq-sidebar sticky-top" style="top: 100px; z-index: 10;">
            
            <div class="search-box p-4 rounded-4 bg-white shadow-sm mb-4 border-0">
              <h5 class="fw-bold text-dark-blue mb-3">¿En qué te ayudamos?</h5>
              <div class="input-group modern-search">
                <span class="input-group-text bg-white border-end-0 text-muted">
                  <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
                </span>
                <input type="text" class="form-control border-start-0 ps-0" placeholder="Buscar palabra clave...">
              </div>
            </div>

            <div class="categories-box p-4 rounded-4 bg-white shadow-sm mb-4 border-0">
              <h5 class="fw-bold text-dark-blue mb-3">Categorías</h5>
              <ul class="nav nav-pills flex-column modern-tabs" id="faqTabs" role="tablist">
                <li v-for="item in navItems" :key="item.id" class="nav-item mb-2" role="presentation">
                  <button class="nav-link w-100 text-start fw-medium d-flex justify-content-between align-items-center" 
                          :class="{ active: item.active }" 
                          :id="`${item.id}-tab`"
                          data-bs-toggle="tab" 
                          :data-bs-target="`#${item.id}`" 
                          type="button" role="tab"
                          :aria-controls="item.id" 
                          :aria-selected="item.active">
                    {{ item.label }}
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="tab-icon"><polyline points="9 18 15 12 9 6"></polyline></svg>
                  </button>
                </li>
              </ul>
            </div>

            <div class="contact-box p-4 rounded-4 bg-red-primary text-white shadow-sm">
              <h5 class="fw-bold mb-2">¿Aún tienes dudas?</h5>
              <p class="small mb-4" style="color: #ffe4e6;">Nuestro equipo de atención al postulante está listo para ayudarte en tu proceso.</p>
              <nuxt-link to="/contacto" class="btn btn-light text-red-primary w-100 fw-bold rounded-pill">
                Contactar Asesor
              </nuxt-link>
            </div>

          </div>
        </div>

        <div class="col-lg-8">
          <div class="tab-content" id="faqTabContent">
            
            <div v-for="tab in tabContentData" :key="tab.id" 
                 class="tab-pane fade" :class="{ 'show active': tab.id === 'admision' }" 
                 :id="tab.id" role="tabpanel" :aria-labelledby="`${tab.id}-tab`">
              
              <h4 class="fw-bold mb-4 text-dark-blue">{{ tab.title }}</h4>
              
              <div class="accordion modern-accordion" :id="`accordion-${tab.id}`">
                <div v-for="(faq, index) in tab.faqs" :key="faq.id" class="accordion-item mb-3 border-0 bg-transparent">
                  <h2 class="accordion-header" :id="`heading-${faq.id}`">
                    <button class="accordion-button rounded-3 fw-semibold text-dark-blue shadow-sm" 
                            :class="{ 'collapsed': !faq.active }" 
                            type="button" data-bs-toggle="collapse" 
                            :data-bs-target="`#collapse-${faq.id}`" 
                            :aria-expanded="faq.active ? 'true' : 'false'" 
                            :aria-controls="`collapse-${faq.id}`">
                      {{ faq.question }}
                    </button>
                  </h2>
                  <div :id="`collapse-${faq.id}`" 
                       class="accordion-collapse collapse" 
                       :class="{ 'show': faq.active }" 
                       :aria-labelledby="`heading-${faq.id}`" 
                       :data-bs-parent="`#accordion-${tab.id}`">
                    <div class="accordion-body bg-white rounded-bottom-3 mt-1 shadow-sm text-muted">
                      {{ faq.answer }}
                    </div>
                  </div>
                </div>
              </div>

            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Categorías de Navegación
const navItems = [
  { id: "admision", label: "Proceso de Admisión", active: true },
  { id: "requisitos", label: "Requisitos y Pagos", active: false },
  { id: "programas", label: "Programas de Estudio", active: false },
];

// Datos del Contenido (Preguntas y Respuestas)
const tabContentData = [
  {
    id: "admision",
    title: "Sobre el Proceso de Admisión",
    faqs: [
      {
        id: 101,
        active: true,
        question: "¿Cuáles son las fechas del próximo Examen General?",
        answer: "El Examen General 2026 - I se llevará a cabo los días 14 y 15 de marzo de 2026. Recuerda que las preinscripciones virtuales finalizan el 10 de marzo. Te recomendamos realizar tu proceso con anticipación para evitar inconvenientes.",
      },
      {
        id: 102,
        active: false,
        question: "¿Dónde se realiza el examen y qué debo llevar?",
        answer: "El examen es estrictamente presencial y se rinde en el campus principal de nuestra institución. Debes asistir portando únicamente tu DNI original vigente, tu carnet de postulante impreso, un lápiz 2B, borrador y tajador. No se permite el ingreso de dispositivos electrónicos.",
      },
      {
        id: 103,
        active: false,
        question: "¿Existen modalidades de ingreso directo?",
        answer: "Sí, contamos con ingreso directo para los estudiantes que ocupen los primeros puestos en nuestra CEPRE (Centro Preuniversitario) al finalizar el ciclo correspondiente, además de modalidades extraordinarias para deportistas calificados y primeros puestos de educación secundaria.",
      },
    ],
  },
  {
    id: "requisitos",
    title: "Requisitos Documentarios y Pagos",
    faqs: [
      {
        id: 201,
        active: true,
        question: "¿Qué documentos necesito para validar mi inscripción?",
        answer: "Para completar tu inscripción presencial necesitas: DNI original y copia, Certificado de Estudios Secundarios (original), partida de nacimiento original, dos fotografías tamaño carnet (fondo blanco) y el comprobante de pago por derecho de admisión.",
      },
      {
        id: 202,
        active: false,
        question: "¿Cuánto es el costo por derecho de admisión?",
        answer: "El costo varía según el colegio de procedencia. Para egresados de colegios nacionales el costo es de S/ 250.00, mientras que para colegios particulares es de S/ 350.00. Los pagos se realizan únicamente en las cuentas bancarias oficiales de la institución.",
      },
      {
        id: 203,
        active: false,
        question: "¿Puedo pedir devolución si decido no postular?",
        answer: "Según el reglamento general de admisión, una vez efectuado el pago y registrada la preinscripción, no hay lugar a devoluciones por ningún motivo ni se puede transferir el derecho a otra persona o para un proceso futuro.",
      },
    ],
  },
  {
    id: "programas",
    title: "Programas de Estudio y Vida Académica",
    faqs: [
      {
        id: 301,
        active: true,
        question: "¿Cuántos años dura una carrera técnica en la institución?",
        answer: "Todos nuestros Programas de Estudio tienen una duración de 3 años académicos, divididos en 6 semestres. Al finalizar y cumplir con los requisitos, obtienes el Título a Nombre de la Nación como Profesional Técnico.",
      },
      {
        id: 302,
        active: false,
        question: "¿Tienen convenios para realizar prácticas pre-profesionales?",
        answer: "¡Por supuesto! Tenemos convenios activos con importantes empresas e instituciones de la región, lo que garantiza que nuestros estudiantes puedan aplicar sus conocimientos en el campo laboral desde los primeros semestres, especialmente en áreas de evaluación de proyectos y gestión ambiental.",
      },
    ],
  },
];
</script>

<style scoped>
/* Fondo general sutil */
.bg-light-gray {
  background-color: #f8fafc;
}

/* Tipografía y colores */
.text-dark-blue { color: #0f172a; }
.bg-red-primary { background-color: #e11d48; }
.text-red-primary { color: #e11d48; }

.section-title {
  font-family: 'Inter', system-ui, sans-serif;
  letter-spacing: -0.5px;
}

/* Buscador Moderno */
.modern-search .form-control, 
.modern-search .input-group-text {
  border-color: #e2e8f0;
  padding: 12px 16px;
  box-shadow: none;
}
.modern-search .form-control:focus {
  border-color: #e11d48;
  box-shadow: none;
}
.modern-search .input-group-text {
  background-color: #fff;
}
.modern-search:focus-within .input-group-text {
  border-color: #e11d48;
  color: #e11d48 !important;
}

/* Tabs Laterales (Navegación) */
.modern-tabs .nav-link {
  color: #475569;
  background-color: transparent;
  border-radius: 12px;
  padding: 14px 20px;
  transition: all 0.3s ease;
}
.modern-tabs .nav-link:hover {
  background-color: #f1f5f9;
  color: #1e293b;
}
.modern-tabs .nav-link.active {
  background-color: #fff1f2;
  color: #be123c;
}
.tab-icon {
  transition: transform 0.3s ease;
  opacity: 0.5;
}
.modern-tabs .nav-link.active .tab-icon {
  transform: translateX(4px);
  opacity: 1;
  color: #e11d48;
}

/* Acordeón Moderno */
.modern-accordion .accordion-button {
  background-color: #ffffff;
  border: 1px solid #e2e8f0;
  padding: 18px 24px;
  font-size: 1.05rem;
}
.modern-accordion .accordion-button:not(.collapsed) {
  background-color: #e11d48;
  color: #ffffff !important;
  border-color: #e11d48;
  box-shadow: 0 8px 20px rgba(225, 29, 72, 0.2);
}
.modern-accordion .accordion-button::after {
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23475569' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpolyline points='6 9 12 15 18 9'%3E%3C/polyline%3E%3C/svg%3E");
}
.modern-accordion .accordion-button:not(.collapsed)::after {
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%23ffffff' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpolyline points='18 15 12 9 6 15'%3E%3C/polyline%3E%3C/svg%3E");
}
.modern-accordion .accordion-body {
  padding: 24px;
  border: 1px solid #e2e8f0;
  border-top: none;
  font-size: 1.05rem;
  line-height: 1.6;
}
</style>