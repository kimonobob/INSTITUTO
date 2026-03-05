<template>
  <section class="exam-guide-area py-5">
    <div class="container">
      <div class="text-center mb-5">
        <h6 class="text-danger fw-bold text-uppercase tracking-wider mb-2">IESTP AYAVIRI</h6>
        <h2 class="exam-title">EXAMEN DE ADMISIÓN ORDINARIO 2026</h2>
        <p class="text-muted fs-5">¿No sabes por dónde empezar? Aquí te guiamos paso a paso.</p>
      </div>

      <div class="card modern-card border-0 p-4 p-md-5">

        <div class="stepper-wrapper d-flex justify-content-between mb-5 position-relative">
          <div class="step-divider"></div>
          
          <div class="step-item active">
            <div class="step-circle">1</div>
            <div class="step-text">
              <span class="step-title">Convocatoria y Preinscripción / Inscripción</span>
              <span class="step-date"><span class="active-dot"></span> 02-mar. – 07-abr. / 09-mar. – 07-abr.</span>
            </div>
          </div>

          <div class="step-item inactive">
            <div class="step-circle">2</div>
            <div class="step-text">
              <span class="step-title">Inscripción Exonerados y Extraordinario</span>
              <span class="step-date">09-mar. – 05-abr.</span>
            </div>
          </div>

          <div class="step-item inactive">
            <div class="step-circle">3</div>
            <div class="step-text">
              <span class="step-title">Examen por Exoneración</span>
              <span class="step-date">06 abr. 2026</span>
            </div>
          </div>

          <div class="step-item inactive">
            <div class="step-circle">4</div>
            <div class="step-text">
              <span class="step-title">Examen Extraordinario</span>
              <span class="step-date">07 abr. 2026</span>
            </div>
          </div>

          <div class="step-item inactive">
            <div class="step-circle">5</div>
            <div class="step-text">
              <span class="step-title">Examen Ordinario y Publicación de Resultados</span>
              <span class="step-date">08 abr. 2026</span>
            </div>
          </div>
        </div>

        <div class="guide-header mb-4">
          <h5 class="guide-title m-0">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="me-2"><circle cx="12" cy="12" r="10"></circle><line x1="12" y1="16" x2="12" y2="12"></line><line x1="12" y1="8" x2="12.01" y2="8"></line></svg>
            Guía rápida (para no perderte)
          </h5>
        </div>

        <div class="row g-4">
          <div class="col-lg-5">
            <h6 class="fw-bold mb-3 text-dark-red">1) ¿Qué etapa está activa hoy?</h6>
            <div class="d-flex flex-column gap-3 mb-3 align-items-start">
              <span class="badge-custom">Convocatoria activa</span>
              <span class="badge-custom">Inscripción activa (presencial en Mesa de Partes)</span>
            </div>
            <p class="text-muted small mt-4">
              Si ves "<span class="active-dot-inline"></span>" en una fecha, significa que esa etapa está activa hoy.
            </p>
          </div>

          <div class="col-lg-7">
            <div class="bg-light-red p-4 rounded-4 modern-box">
              <h6 class="fw-bold mb-3 text-dark-red">2) ¿Qué debo hacer ahora?</h6>
              <ul class="task-list mb-4">
                <li>Realiza la inscripción en Mesa de Partes del IESTP Ayaviri con tus documentos.</li>
                <li>Paga el derecho de admisión (Banco de la Nación o caja institucional).</li>
                <li>Revisa los requisitos exigidos (DNI, certificado SIAGIE, foto, voucher de pago).</li>
                <li>Prepárate para el examen ordinario el 08 de abril en el Coliseo cerrado.</li>
              </ul>
              
              <div class="d-flex gap-3 flex-wrap mt-4">
                <nuxt-link to="/pre-inscripcion" class="btn btn-red-primary px-4 py-2 rounded-pill fw-bold">
                  Iniciar Inscripción
                </nuxt-link>
                <a href="/documentos/Prospectoadmisión2026.pdf" target="_blank" rel="noopener noreferrer" class="btn btn-red-outline px-4 py-2 rounded-pill fw-bold">
  Ver Prospecto
</a>
              </div>
            </div>
          </div>
        </div>

        <div class="alert-custom mt-5 p-4 rounded-4 d-flex align-items-center gap-3">
          <div class="alert-icon">
             <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"></path><line x1="12" y1="9" x2="12" y2="13"></line><line x1="12" y1="17" x2="12.01" y2="17"></line></svg>
          </div>
          <div>
            <h6 class="fw-bold mb-1 text-dark-red">Importante</h6>
            <p class="m-0 text-muted">La <strong>Inscripción</strong> se realiza de forma <strong>presencial</strong> en la <strong>Mesa de Partes del IESTP Ayaviri</strong>. Lleva tu DNI y los requisitos solicitados.</p>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
/* Tipografía moderna y color rojo oscuro */
.exam-title {
  color: #881337; /* Rojo muy oscuro, elegante */
  font-family: 'Inter', system-ui, -apple-system, sans-serif;
  font-weight: 800;
  letter-spacing: -0.5px;
}
.tracking-wider {
  letter-spacing: 0.05em;
}
.text-dark-red {
  color: #9f1239;
}

/* Tarjeta principal con sombra moderna */
.modern-card {
  border-radius: 24px;
  box-shadow: 0 20px 40px rgba(159, 18, 57, 0.05), 0 1px 3px rgba(0,0,0,0.05);
  background: #ffffff;
}

/* Stepper (Línea de tiempo) */
.stepper-wrapper {
  margin-top: 1rem;
}
.step-divider {
  position: absolute;
  top: 18px;
  left: 10%;
  right: 10%;
  height: 2px;
  background-color: #fce7f3; /* Rosa/Rojo muy claro */
  z-index: 1;
}
.step-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  z-index: 2;
  background-color: #fff;
  padding: 0 15px;
  flex: 1;
}
.step-circle {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 15px;
  margin-bottom: 12px;
  transition: all 0.3s ease;
}
.step-item.active .step-circle {
  background-color: #e11d48; /* Rojo vibrante */
  color: white;
  box-shadow: 0 0 0 6px #ffe4e6; /* Efecto de halo moderno */
}
.step-item.inactive .step-circle {
  background-color: #f8fafc;
  color: #94a3b8;
  border: 2px solid #e2e8f0;
}
.step-title {
  font-weight: 700;
  font-size: 14px;
  color: #1e293b;
  display: block;
  line-height: 1.3;
  margin-bottom: 6px;
}
.step-item.inactive .step-title {
  color: #94a3b8;
}
.step-date {
  font-size: 13px;
  color: #64748b;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  font-weight: 500;
}

/* Indicador de activo (Mantenemos verde para semántica de UI) */
.active-dot {
  width: 10px;
  height: 10px;
  background-color: #10b981; /* Verde moderno */
  border-radius: 50%;
  display: inline-block;
  box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.2);
}
.active-dot-inline {
  width: 12px;
  height: 12px;
  background-color: #10b981;
  border-radius: 50%;
  display: inline-block;
  vertical-align: middle;
}

/* Separador y Títulos de Guía */
.guide-header {
  border-bottom: 2px dashed #fce7f3;
  padding-bottom: 1.5rem;
}
.guide-title {
  color: #be123c;
  font-weight: 800;
  display: flex;
  align-items: center;
}

/* Badges */
.badge-custom {
  background-color: #fff1f2;
  color: #be123c;
  border: 1px solid #fecdd3;
  padding: 8px 16px;
  border-radius: 12px;
  font-size: 14px;
  font-weight: 600;
  box-shadow: 0 2px 4px rgba(190, 18, 60, 0.05);
}

/* Caja derecha moderna */
.bg-light-red {
  background-color: #fffbfa;
  border: 1px solid #ffe4e6;
}
.modern-box {
  box-shadow: inset 0 2px 4px rgba(0,0,0,0.02);
}

/* Lista de tareas */
.task-list {
  padding-left: 1.2rem;
  color: #475569;
  font-size: 15px;
  line-height: 1.7;
}
.task-list li::marker {
  color: #e11d48;
}

/* Botones Modernos */
.btn-red-primary {
  background-color: #e11d48;
  color: white;
  border: none;
  transition: all 0.3s ease;
  box-shadow: 0 4px 12px rgba(225, 29, 72, 0.2);
}
.btn-red-primary:hover {
  background-color: #be123c;
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(225, 29, 72, 0.3);
  color: white;
}
.btn-red-outline {
  background-color: white;
  color: #e11d48;
  border: 2px solid #e11d48;
  transition: all 0.3s ease;
}
.btn-red-outline:hover {
  background-color: #fff1f2;
  color: #be123c;
}

/* Alerta del footer */
.alert-custom {
  background-color: #fff1f2;
  border: 1px solid #fecdd3;
}
.alert-icon {
  color: #e11d48;
  background: white;
  padding: 10px;
  border-radius: 50%;
  box-shadow: 0 2px 8px rgba(225, 29, 72, 0.15);
}
</style>