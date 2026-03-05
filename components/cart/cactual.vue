<template>
  <section class="convocatorias-area py-5 bg-light-gray">
    <div class="container">
      
      <div class="text-center mb-5">
        <h2 class="section-title d-flex justify-content-center align-items-center gap-3">
          Convocatorias Vigentes
          <span class="badge bg-red-primary text-white rounded-pill fs-6 px-3 py-1 shadow-sm">Nuevo</span>
        </h2>
        <p class="text-muted fs-5">Selecciona el proceso de admisión que se ajuste a tu perfil</p>
      </div>

      <div class="card featured-card border-0 mb-5 overflow-hidden">
        <div class="row g-0">
          
          <div class="col-lg-7 p-4 p-md-5 d-flex flex-column justify-content-center">
            
            <div class="d-flex align-items-center gap-2 mb-3">
              <span class="badge bg-red-light text-red-dark border border-red px-3 py-2 rounded-pill fw-bold">Principal</span>
              <span class="badge border border-success text-success px-3 py-2 rounded-pill fw-bold d-flex align-items-center gap-1">
                <span class="active-dot-green"></span> Activo
              </span>
            </div>

            <h3 class="fw-bolder mb-4 text-dark-blue" style="font-size: 2rem;">EXAMEN GENERAL 2026 - I</h3>

            <ul class="list-unstyled mb-4 dates-list">
              <li><strong>Preinscripciones:</strong> 23 feb. 2026 - 10 mar. 2026</li>
              <li><strong>Inscripciones:</strong> 02 mar. 2026 - 10 mar. 2026</li>
              <li><strong>Examen:</strong> 14 mar. 2026 - 15 mar. 2026</li>
            </ul>

            <h6 class="fw-bold text-muted mb-3">Acciones Rápidas</h6>
            <div class="row g-3 mb-5">
              <div class="col-sm-6">
                <a href="#" class="quick-action-btn">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line><polyline points="10 9 9 9 8 9"></polyline></svg>
                  Requisitos
                </a>
              </div>
              <div class="col-sm-6">
                <a href="#" class="quick-action-btn">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="5" width="20" height="14" rx="2" ry="2"></rect><line x1="2" y1="10" x2="22" y2="10"></line></svg>
                  Pagos
                </a>
              </div>
              <div class="col-sm-6">
                <a href="#" class="quick-action-btn">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path><circle cx="9" cy="7" r="4"></circle><path d="M23 21v-2a4 4 0 0 0-3-3.87"></path><path d="M16 3.13a4 4 0 0 1 0 7.75"></path></svg>
                  Vacantes
                </a>
              </div>
              <div class="col-sm-6">
                <a href="#" class="quick-action-btn">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect><line x1="16" y1="2" x2="16" y2="6"></line><line x1="8" y1="2" x2="8" y2="6"></line><line x1="3" y1="10" x2="21" y2="10"></line></svg>
                  Cronograma
                </a>
              </div>
            </div>

            <div class="cta-box p-4 rounded-4 d-flex flex-column flex-sm-row align-items-center justify-content-between gap-3">
              <div>
                <h6 class="fw-bold mb-1 text-dark-red">Preinscripción en Línea</h6>
                <p class="m-0 text-muted small">Completa tu preinscripción de manera virtual y segura</p>
              </div>
              <nuxt-link to="/pre-inscripcion" class="btn btn-red-primary px-4 py-3 rounded-pill fw-bold text-nowrap shadow-sm d-flex align-items-center gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"></path><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"></path></svg>
                Iniciar Preinscripción
              </nuxt-link>
            </div>

          </div>

          <div class="col-lg-5 flyer-container d-none d-lg-block position-relative">
            <img src="/images/flyer-admision.jpg" alt="Afiche Admisión 2026" class="img-fluid h-100 w-100 object-fit-cover">
            <div class="flyer-overlay"></div>
          </div>
        </div>
      </div>

      <div class="row g-4">
        <div class="col-md-6">
          <div class="card secondary-card border-0 p-4 h-100">
            <div class="d-flex justify-content-between align-items-start mb-3">
              <h5 class="fw-bold text-muted m-0">Extraordinario</h5>
              <span class="badge bg-light text-secondary border px-3 py-2 rounded-pill">Finalizado</span>
            </div>
            <p class="text-secondary fw-medium mb-1"><i class="bi bi-calendar3"></i> 30 de enero</p>
            <p class="text-muted small m-0">Modalidad extraordinaria para perfiles específicos</p>
          </div>
        </div>

        <div class="col-md-6">
          <div class="card secondary-card border-0 p-4 h-100">
            <div class="d-flex justify-content-between align-items-start mb-3">
              <h5 class="fw-bold text-muted m-0">CEPREUNA</h5>
              <span class="badge bg-light text-secondary border px-3 py-2 rounded-pill">Finalizado</span>
            </div>
            <p class="text-secondary fw-medium mb-1"><i class="bi bi-calendar3"></i> 10 y 11 de enero</p>
            <p class="text-muted small m-0">Postulantes del CEPREUNA</p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* Fondo general sutil */
.bg-light-gray {
  background-color: #f8fafc;
  background-image: radial-gradient(#e2e8f0 1px, transparent 1px);
  background-size: 20px 20px; /* Le da el efecto de cuadrícula sutil como en tu imagen */
}

/* Títulos */
.section-title {
  color: #1e293b;
  font-family: 'Inter', system-ui, sans-serif;
  font-weight: 800;
  letter-spacing: -0.5px;
}
.text-dark-blue {
  color: #0f172a;
}
.text-dark-red {
  color: #9f1239;
}

/* Colores Rojos Temáticos */
.bg-red-primary { background-color: #e11d48; }
.bg-red-light { background-color: #fff1f2; }
.text-red-dark { color: #be123c; }
.border-red { border-color: #fecdd3 !important; }

/* Indicador Verde */
.active-dot-green {
  width: 8px;
  height: 8px;
  background-color: #10b981;
  border-radius: 50%;
  display: inline-block;
  box-shadow: 0 0 0 2px rgba(16, 185, 129, 0.2);
}

/* Tarjeta Principal */
.featured-card {
  border-radius: 24px;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.04), 0 1px 3px rgba(0,0,0,0.02);
  background: #ffffff;
}

/* Lista de Fechas */
.dates-list {
  color: #475569;
  font-size: 1.05rem;
}
.dates-list li {
  margin-bottom: 0.5rem;
}
.dates-list strong {
  color: #1e293b;
  width: 140px;
  display: inline-block;
}

/* Botones de Acciones Rápidas (El "mejorado") */
.quick-action-btn {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 14px 20px;
  background-color: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  color: #334155;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.2s ease;
}
.quick-action-btn:hover {
  background-color: #fff1f2;
  border-color: #fecdd3;
  color: #be123c;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(190, 18, 60, 0.05);
}
.quick-action-btn svg {
  color: #94a3b8;
  transition: color 0.2s ease;
}
.quick-action-btn:hover svg {
  color: #e11d48;
}

/* Caja de Preinscripción CTA */
.cta-box {
  background-color: #fffbfa;
  border: 1px solid #ffe4e6;
  border-left: 4px solid #e11d48;
}

/* Botón Rojo Principal */
.btn-red-primary {
  background-color: #e11d48;
  color: white;
  border: none;
  transition: all 0.3s ease;
}
.btn-red-primary:hover {
  background-color: #be123c;
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(225, 29, 72, 0.25) !important;
  color: white;
}

/* Imagen del Afiche */
.flyer-container {
  background-color: #f1f5f9;
}
.object-fit-cover {
  object-fit: cover;
  object-position: center;
}
.flyer-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to right, rgba(255,255,255,1) 0%, rgba(255,255,255,0) 15%);
}

/* Tarjetas Secundarias (Finalizadas) */
.secondary-card {
  border-radius: 20px;
  background-color: #ffffff;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.02);
  opacity: 0.85; /* Las hace ver un poco menos relevantes */
  transition: opacity 0.3s ease;
}
.secondary-card:hover {
  opacity: 1;
}
</style>