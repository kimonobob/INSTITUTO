<template>
  <div class="pre-inscription-page bg-light-gray min-vh-100 pb-5">
    
    <header class="form-header text-center py-5 mb-4 position-relative overflow-hidden">
      <div class="container position-relative z-2">
        <h2 class="text-white fw-bold mb-1">EXAMEN GENERAL 2026-I</h2>
        <div class="d-inline-flex align-items-center gap-3">
          <hr class="header-line">
          <h4 class="text-white mb-0 fw-light">Preinscripción</h4>
          <hr class="header-line">
        </div>
      </div>
      <div class="header-bg"></div>
    </header>

    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-10">
          
          <div class="card shadow-lg border-0 rounded-4 overflow-hidden">
            <div class="card-body p-4 p-md-5">

              <transition name="fade" mode="out-in">
                
                <div v-if="currentStep === 1" key="step1" class="form-step">
                  <h5 class="fw-bold mb-4 text-dark-blue">Datos personales</h5>
                  
                  <div class="row g-4">
                    <div class="col-12 d-flex justify-content-md-end gap-4 mb-2">
                      <div>
                        <label class="form-label text-muted small fw-semibold mb-2">Sexo</label>
                        <div class="d-flex gap-3">
                          <div class="form-check">
                            <input class="form-check-input custom-radio" type="radio" name="sexo" id="sexoM" value="M" v-model="formData.sexo">
                            <label class="form-check-label" for="sexoM">M</label>
                          </div>
                          <div class="form-check">
                            <input class="form-check-input custom-radio" type="radio" name="sexo" id="sexoF" value="F" v-model="formData.sexo">
                            <label class="form-check-label" for="sexoF">F</label>
                          </div>
                        </div>
                      </div>
                      <div style="min-width: 150px;">
                        <label class="form-label text-muted small fw-semibold mb-2">Estado civil</label>
                        <select class="form-select modern-input" v-model="formData.estadoCivil">
                          <option value="Soltero">Soltero(a)</option>
                          <option value="Casado">Casado(a)</option>
                          <option value="Divorciado">Divorciado(a)</option>
                          <option value="Viudo">Viudo(a)</option>
                        </select>
                      </div>
                    </div>

                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Primer apellido <span class="text-danger">*</span></label>
                      <input type="text" class="form-control modern-input" v-model="formData.primerApellido" @input="forceLetters('primerApellido')" placeholder="Ej: SALAMANCA">
                    </div>
                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Segundo apellido</label>
                      <input type="text" class="form-control modern-input" v-model="formData.segundoApellido" @input="forceLetters('segundoApellido')" placeholder="Ej: GUTIERREZ">
                    </div>
                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Pre Nombres <span class="text-danger">*</span></label>
                      <input type="text" class="form-control modern-input" v-model="formData.nombres" @input="forceLetters('nombres')" placeholder="Ej: ALBERTO JULIAN">
                    </div>

                    <div class="col-md-6">
                      <label class="form-label text-muted small fw-semibold">Correo electrónico <span class="text-danger">*</span></label>
                      <input type="email" class="form-control modern-input" v-model="formData.correo" placeholder="ejemplo@correo.com">
                    </div>
                    
                    <div class="col-md-6">
                      <div class="d-flex justify-content-between">
                        <label class="form-label text-muted small fw-semibold">Ubigeo de nacimiento <span class="text-danger">*</span></label>
                        <a href="#" @click.prevent="openUbigeoModal" class="text-red-primary small text-decoration-none">
                          <i class="bi bi-info-circle me-1"></i>ver ejemplo
                        </a>
                      </div>
                      <input type="text" class="form-control modern-input" v-model="formData.ubigeoNacimiento" @input="forceNumbers('ubigeoNacimiento', 6)" placeholder="Ej: 210801">
                    </div>

                    <div class="col-md-6">
                      <label class="form-label text-muted small fw-semibold">Numero de celular <span class="text-danger">*</span></label>
                      <input type="tel" class="form-control modern-input" v-model="formData.celular" @input="forceNumbers('celular', 9)" placeholder="Ej: 989931048">
                    </div>
                    <div class="col-md-6">
                      <label class="form-label text-muted small fw-semibold">Fec. Nacimiento <span class="text-danger">*</span> "dd/mm/aaaa"</label>
                      <input type="date" class="form-control modern-input" v-model="formData.fechaNacimiento">
                    </div>
                  </div>
                </div>

                <div v-else-if="currentStep === 2" key="step2" class="form-step">
                  <h5 class="fw-bold mb-4 text-dark-blue">Datos de residencia</h5>
                  
                  <div class="row g-4">
                    <div class="col-12">
                      <label class="form-label text-muted small fw-semibold">País:</label>
                      <select class="form-select modern-input" v-model="formData.pais" @change="onDepartamentoChange">
                        <option value="PERÚ">PERÚ</option>
                        <option value="OTRO">OTRO</option>
                      </select>
                    </div>

                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Departamento:</label>
                      <select class="form-select modern-input" v-model="formData.departamento" @change="onDepartamentoChange" :disabled="formData.pais !== 'PERÚ'">
                        <option value="">Seleccione...</option>
                        <option v-for="dep in departamentosDisponibles" :key="dep" :value="dep">{{ dep }}</option>
                      </select>
                    </div>
                    
                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Provincia:</label>
                      <select class="form-select modern-input" v-model="formData.provincia" @change="onProvinciaChange" :disabled="!formData.departamento">
                        <option value="">Seleccione...</option>
                        <option v-for="prov in provinciasDisponibles" :key="prov" :value="prov">{{ prov }}</option>
                      </select>
                    </div>

                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Distrito:</label>
                      <select class="form-select modern-input" v-model="formData.distrito" :disabled="!formData.provincia">
                        <option value="">Seleccione...</option>
                        <option v-for="dist in distritosDisponibles" :key="dist" :value="dist">{{ dist }}</option>
                      </select>
                    </div>

                    <div class="col-12">
                      <label class="form-label text-muted small fw-semibold">Dirección:</label>
                      <input type="text" class="form-control modern-input" v-model="formData.direccion" @input="forceUppercase('direccion')" placeholder="Ej: JR. TARAPACA 331">
                    </div>
                  </div>
                </div>

                <div v-else-if="currentStep === 3" key="step3" class="form-step">
                  <h5 class="fw-bold mb-4 text-dark-blue">DATOS DE EDUCACIÓN SECUNDARIA</h5>
                  
                  <div class="row g-4">
                    <div class="col-12">
                      <label class="form-label text-muted small fw-semibold">Año de egreso:</label>
                     <input type="number" class="form-control modern-input" v-model="formData.anioEgreso" @input="forceNumbers('anioEgreso', 4)" placeholder="Ej: 2019" min="1950" max="2026">
                    </div>

                    <div class="col-12">
                      <label class="form-label text-muted small fw-semibold">País:</label>
                      <select class="form-select modern-input" v-model="formData.paisColegio" @change="onDepartamentoColegioChange">
                        <option value="PERÚ">PERÚ</option>
                        <option value="OTRO">OTRO</option>
                      </select>
                    </div>

                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Departamento:</label>
                      <select class="form-select modern-input" v-model="formData.departamentoColegio" @change="onDepartamentoColegioChange" :disabled="formData.paisColegio !== 'PERÚ'">
                        <option value="">Seleccione...</option>
                        <option v-for="dep in departamentosDisponibles" :key="dep" :value="dep">{{ dep }}</option>
                      </select>
                    </div>
                    
                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Provincia:</label>
                      <select class="form-select modern-input" v-model="formData.provinciaColegio" @change="onProvinciaColegioChange" :disabled="!formData.departamentoColegio">
                        <option value="">Seleccione...</option>
                        <option v-for="prov in provinciasColegioDisponibles" :key="prov" :value="prov">{{ prov }}</option>
                      </select>
                    </div>

                    <div class="col-md-4">
                      <label class="form-label text-muted small fw-semibold">Distrito:</label>
                      <select class="form-select modern-input" v-model="formData.distritoColegio" @change="onDistritoColegioChange" :disabled="!formData.provinciaColegio">
                        <option value="">Seleccione...</option>
                        <option v-for="dist in distritosColegioDisponibles" :key="dist" :value="dist">{{ dist }}</option>
                      </select>
                    </div>

                    <div class="col-12">
                      <label class="form-label text-muted small fw-semibold">Nombre de colegio:</label>
                      <select class="form-select modern-input" v-model="formData.nombreColegio" :disabled="!formData.distritoColegio">
                        <option value="">Seleccione un colegio...</option>
                        <option v-for="colegio in colegiosDisponibles" :key="colegio" :value="colegio">{{ colegio }}</option>
                      </select>
                    </div>
                  </div>
                </div>

                <div v-else-if="currentStep === 4" key="step4" class="form-step">
                  <h5 class="fw-bold mb-4 text-dark-blue">Datos Familiares</h5>
                  
                  <div class="p-4 rounded-4 mb-4" style="background-color: #f8fafc; border: 1px solid #e2e8f0;">
                    <h6 class="fw-bold text-dark-blue mb-3">Datos del apoderado</h6>
                    <div class="row g-3">
                      <div class="col-md-4">
                        <label class="form-label text-muted small fw-semibold">N° Documento:</label>
                       <input type="text" class="form-control modern-input bg-white" v-model="formData.madreDocumento" @input="forceNumbers('madreDocumento', 8)" placeholder="Ej: 02429151">
                      </div>
                      <div class="col-md-8">
                        <label class="form-label text-muted small fw-semibold">Pre nombres:</label>
                        <input type="text" class="form-control modern-input bg-white" v-model="formData.madreNombres" @input="forceLetters('madreNombres')" placeholder="Ej: ALICIA LUISA">
                      </div>
                      <div class="col-12">
                        <label class="form-label text-muted small fw-semibold">Primer apellido:</label>
                        <input type="text" class="form-control modern-input bg-white" v-model="formData.madrePrimerApellido" @input="forceLetters('madrePrimerApellido')" placeholder="Ej: VILLANUEVA">
                      </div>
                      <div class="col-12">
                        <label class="form-label text-muted small fw-semibold">Segundo Apellido:</label>
                        <input type="text" class="form-control modern-input bg-white" v-model="formData.madreSegundoApellido" @input="forceLetters('madreSegundoApellido')" placeholder="Ej: TOVAR">
                      </div>
                    </div>
                  </div>
                </div>
                
                <div v-else-if="currentStep === 5" key="step5" class="form-step">
                  <h5 class="fw-bold mb-4 text-dark-blue">Datos Postulación</h5>
                  
                  <div class="row g-4 p-4 rounded-4" style="background-color: #ffffff; border: 1px solid #e2e8f0;">
                    
                    <div class="col-12 d-flex justify-content-md-end mb-2">
                      <div style="min-width: 250px;">
                        <label class="form-label text-muted small fw-semibold">Modalidad</label>
                        <select class="form-select modern-input" v-model="formData.modalidad">
                          <option v-for="mod in modalidades" :key="mod" :value="mod">{{ mod }}</option>
                        </select>
                      </div>
                    </div>

                    <div class="col-12">
                      <label class="form-label text-muted small fw-semibold">Programa de estudios <span class="text-danger">*</span></label>
                      <select class="form-select modern-input" v-model="formData.programaEstudio">
                        <option value="">Seleccione el programa al que postula...</option>
                        <option v-for="prog in programasEstudio" :key="prog" :value="prog">{{ prog }}</option>
                      </select>
                    </div>

                    <div class="col-md-6">
                      <label class="form-label text-muted small fw-semibold">Tipo certificado:</label>
                      <select class="form-select modern-input" v-model="formData.tipoCertificado">
                        <option value="">Seleccionar tipo de certificado</option>
                        <option v-for="tipo in tiposCertificado" :key="tipo" :value="tipo">{{ tipo }}</option>
                      </select>
                    </div>
                    
                    <div class="col-md-6">
                      <div class="d-flex justify-content-between">
                        <label class="form-label text-muted small fw-semibold">Código certificado</label>
                        <a href="#" @click.prevent="openCertificadoModal" class="text-red-primary small text-decoration-none">
                          <i class="bi bi-info-circle me-1"></i>ver ejemplo
                        </a>
                      </div>
                      <input type="text" class="form-control modern-input" v-model="formData.codigoCertificado" @input="forceUppercase('codigoCertificado')" placeholder="Ej: CE-123456789">
                    </div>

                    <div class="col-12 border-top pt-4 mt-2">
                      <div class="d-flex justify-content-between">
                        <label class="form-label text-muted small fw-bold">Código de pago (Voucher) <span class="text-danger">*</span></label>
                        <a href="#" class="text-red-primary small text-decoration-none">¿Dónde ubicarlo?</a>
                      </div>
                      <input type="text" class="form-control modern-input" v-model="formData.codigoPago" @input="forceUppercase('codigoPago')" placeholder="Ej: 00012345678" style="border-color: #cbd5e1; background-color: #f8fafc;">
                    </div>

                  </div>
                </div>
              </transition>

            </div>


            
            <div class="card-footer bg-white border-0 p-4 pt-0">
              
    <div class="progress-wrapper mb-4 d-flex align-items-center gap-3">
        <div class="progress w-100" style="height: 6px; border-radius: 10px; background-color: #e2e8f0;">
            <div class="progress-bar bg-red-primary" role="progressbar" :style="{ width: progressBarWidth }" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
        </div>
        <span class="text-muted small fw-bold">{{ progressBarWidth }}</span>
    </div>

    <div v-if="errorMsg" class="alert alert-danger py-2 mb-3 text-center small fw-bold" style="background-color: #fff1f2; color: #be123c; border-color: #fecdd3;">
        {{ errorMsg }}
    </div>

    <div class="d-flex justify-content-between mt-4">
        <button 
            type="button" 
            class="btn btn-outline-secondary px-4 py-2 fw-semibold rounded-3" 
            @click="prevStep" 
            :disabled="currentStep === 1">
            Anterior
        </button>
        
        <button 
            type="button" 
            class="btn btn-red-primary px-5 py-2 fw-semibold rounded-3 shadow-sm" 
            @click="nextStep"
            :disabled="isSubmitting">
            <span v-if="isSubmitting" class="spinner-border spinner-border-sm me-2" role="status" aria-hidden="true"></span>
            {{ currentStep === 5 ? (isSubmitting ? 'Enviando...' : 'Finalizar Preinscripción') : 'Siguiente' }}
        </button>
    </div>

</div>
          </div>

        </div>
      </div>
    </div>
  </div>
<transition name="fade-modal">
      <div v-if="showUbigeoModal" class="custom-modal-overlay" @click="closeUbigeoModal">
        <div class="custom-modal-content bg-white p-4 rounded-4 shadow-lg" style="max-width: 600px;" @click.stop>
          
          <button class="close-modal-btn" @click="closeUbigeoModal">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
          </button>

          <div class="text-center mb-4">
            <h5 class="fw-bold text-dark-blue mb-3">¿Dónde ubico mi código de Ubigeo?</h5>
            <p class="text-muted small mb-3">Selecciona el tipo de DNI que tienes para ver el ejemplo:</p>
            
            <div class="d-flex justify-content-center gap-2 flex-wrap">
              <button 
                class="btn btn-sm rounded-pill fw-bold px-3" 
                :class="activeDniTab === 'azul' ? 'btn-red-primary' : 'btn-outline-secondary'" 
                @click="activeDniTab = 'azul'">
                DNI Azul
              </button>
              <button 
                class="btn btn-sm rounded-pill fw-bold px-3" 
                :class="activeDniTab === 'electronico' ? 'btn-red-primary' : 'btn-outline-secondary'" 
                @click="activeDniTab = 'electronico'">
                DNI Electrónico
              </button>
              <button 
                class="btn btn-sm rounded-pill fw-bold px-3" 
                :class="activeDniTab === 'amarillo' ? 'btn-red-primary' : 'btn-outline-secondary'" 
                @click="activeDniTab = 'amarillo'">
                DNI Amarillo
              </button>
            </div>
          </div>

          <div class="text-center bg-light rounded-3 p-3">
            <transition name="fade" mode="out-in">
              <img :key="activeDniTab" :src="dniImages[activeDniTab]" alt="Ubicación de Ubigeo en DNI" class="img-fluid rounded shadow-sm" style="max-height: 350px;">
            </transition>
          </div>

        </div>
      </div>
    </transition>
<transition name="fade-modal">
      <div v-if="showCertificadoModal" class="custom-modal-overlay" @click="closeCertificadoModal">
        <div class="custom-modal-content bg-white p-4 rounded-4 shadow-lg" style="max-width: 600px;" @click.stop>
          
          <button class="close-modal-btn" @click="closeCertificadoModal">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
          </button>

          <div class="text-center mb-4">
            <h5 class="fw-bold text-dark-blue mb-3">¿Dónde ubico el código de mi certificado?</h5>
            <p class="text-muted small mb-3">Selecciona el tipo de documento que tienes para ver el ejemplo:</p>
            
            <div class="d-flex justify-content-center gap-2 flex-wrap">
              <button 
                class="btn btn-sm rounded-pill fw-bold px-3" 
                :class="activeCertificadoTab === 'amarillo' ? 'btn-red-primary' : 'btn-outline-secondary'" 
                @click="activeCertificadoTab = 'amarillo'">
                Amarillo
              </button>
              <button 
                class="btn btn-sm rounded-pill fw-bold px-3" 
                :class="activeCertificadoTab === 'blanco' ? 'btn-red-primary' : 'btn-outline-secondary'" 
                @click="activeCertificadoTab = 'blanco'">
                Blanco
              </button>
              <button 
                class="btn btn-sm rounded-pill fw-bold px-3" 
                :class="activeCertificadoTab === 'constancia' ? 'btn-red-primary' : 'btn-outline-secondary'" 
                @click="activeCertificadoTab = 'constancia'">
                Constancia (CLA)
              </button>
            </div>
          </div>

          <div class="text-center bg-light rounded-3 p-3">
            <transition name="fade" mode="out-in">
              <img :key="activeCertificadoTab" :src="certificadoImages[activeCertificadoTab]" alt="Ubicación de código en el certificado" class="img-fluid rounded shadow-sm" style="max-height: 350px;">
            </transition>
          </div>

        </div>
      </div>
    </transition>

</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const currentStep = ref(1) 
const totalSteps = 5
const errorMsg = ref('') 
const isSubmitting = ref(false)

// ¡AQUÍ ESTÁ TU ENLACE REAL INTEGRADO!
const scriptURL = 'https://script.google.com/macros/s/AKfycbwqtz6zU_TNBpQGWyKBtrL708wfs_N3pKVpTV26Y-REehkUHihfGmYceCdvrsRGXpdK3g/exec' 

const formData = ref({
  // Paso 1
  sexo: 'M', estadoCivil: 'Soltero', primerApellido: '', segundoApellido: '', nombres: '',
  correo: '', ubigeoNacimiento: '', celular: '', fechaNacimiento: '',
  
  // Paso 2
  pais: 'PERÚ', departamento: '', provincia: '', distrito: '', direccion: '',

  // Paso 3
  anioEgreso: '', paisColegio: 'PERÚ', departamentoColegio: '', provinciaColegio: '',
  distritoColegio: '', nombreColegio: '',

  // Paso 4
  madreDocumento: '', madreNombres: '', madrePrimerApellido: '', madreSegundoApellido: '',
  padreDocumento: '', padreNombres: '', padrePrimerApellido: '', padreSegundoApellido: '',
  
  // Paso 5
  modalidad: 'EXAMEN GENERAL', programaEstudio: '', tipoCertificado: '', codigoCertificado: '',codigoPago: '',
})

// --- DICCIONARIOS ---
const ubigeoData: Record<string, Record<string, string[]>> = {
  "PUNO": {
    "PUNO": ["PUNO", "ACORA", "AMANTANI", "ATUNCOLLA", "CAPACHICA", "CHUCUITO", "COATA", "HUATA", "MAÑAZO", "PAUCARCOLLA", "PICHACANI", "PLATERIA", "SAN ANTONIO", "TIQUILLACA", "VILQUE"],
    "SAN ROMAN": ["JULIACA", "CABANILLAS", "CALAPUJA", "CARACOTO", "SAN MIGUEL"],
    "MELGAR": ["AYAVIRI", "ANTAUTA", "CUPI", "LLALLI", "MACARI", "NUÑOA", "ORURILLO", "SANTA ROSA", "UMACHIRI"],
    "AZANGARO": ["AZANGARO", "ACHAYA", "ARAPA", "ASILLO", "CAMINACA", "CHUPA", "JOSÉ DOMINGO CHOQUEHUANCA", "MUÑANI", "POTONI", "SAMAN", "SAN ANTON", "SAN JOSE", "SAN JUAN DE SALINAS", "SANTIAGO DE PUPUJA", "TIRAPATA"]
  }
}

const colegiosData: Record<string, string[]> = {
  "JULIACA": ["32 MARIANO H. CORNEJO", "POLITECNICO REGIONAL LOS ANDES", "LAS MERCEDES", "SAN ROMAN"],
  "PUNO": ["GLORIOSO SAN CARLOS", "SANTA ROSA", "CARLOS RUBINA BURGOS"],
  "AYAVIRI": ["MARIANO MELGAR", "NUESTRA SEÑORA DE ALTAGRACIA", "SAN FRANCISCO DE ASÍS"]
}

const modalidades = ['ORDINARIO', 'EXONERADO (PRIMEROS PUESTOS)', 'EXTRAORDINARIO']
const programasEstudio = ['Contabilidad', 'Enfermería Técnica', 'Producción Agropecuaria', 'Industrias Alimentarias', 'Arquitectura de Plataformas y Servicios de Tecnologías de Información']
const tiposCertificado = ['Certificado de Estudios (Amarillo)', 'Certificado de Estudios (Blanco)', 'Constancia de Logros de Aprendizaje (CLA)']

// --- LÓGICA DE LA VENTANA FLOTANTE (UBIGEO) ---
const showUbigeoModal = ref(false)
const activeDniTab = ref('azul') // Por defecto arranca mostrando el azul

// Diccionario con las rutas de tus imágenes
const dniImages: Record<string, string> = {
  azul: '/images/admision/dnia.jpg',
  electronico: '/images/admision/dnie.jpg',
  amarillo: '/images/admision/dniam.jpg'
}

const openUbigeoModal = () => {
  activeDniTab.value = 'azul' // Resetea a azul cada vez que se abre
  showUbigeoModal.value = true
}

const closeUbigeoModal = () => {
  showUbigeoModal.value = false
}


// --- LÓGICA DE LA VENTANA FLOTANTE (CERTIFICADOS) ---
const showCertificadoModal = ref(false)
const activeCertificadoTab = ref('amarillo') // Inicia mostrando el certificado amarillo

// Diccionario con las rutas de las imágenes de los certificados
const certificadoImages: Record<string, string> = {
  amarillo: '/images/admision/certia.jpg',
  blanco: '/images/admision/certib.jpg',
  constancia: '/images/admision/constanciae.jpg'
}

const openCertificadoModal = () => {
  activeCertificadoTab.value = 'amarillo' // Resetea a amarillo al abrir
  showCertificadoModal.value = true
}

const closeCertificadoModal = () => {
  showCertificadoModal.value = false
}
// --- LÓGICA DE CASCADA ---
const departamentosDisponibles = computed(() => Object.keys(ubigeoData))
const provinciasDisponibles = computed(() => {
  if (!formData.value.departamento || !ubigeoData[formData.value.departamento]) return []
  return Object.keys(ubigeoData[formData.value.departamento])
})
const distritosDisponibles = computed(() => {
  if (!formData.value.departamento || !formData.value.provincia) return []
  return ubigeoData[formData.value.departamento][formData.value.provincia] || []
})
const onDepartamentoChange = () => { formData.value.provincia = ''; formData.value.distrito = '' }
const onProvinciaChange = () => { formData.value.distrito = '' }

const provinciasColegioDisponibles = computed(() => {
  if (!formData.value.departamentoColegio || !ubigeoData[formData.value.departamentoColegio]) return []
  return Object.keys(ubigeoData[formData.value.departamentoColegio])
})
const distritosColegioDisponibles = computed(() => {
  if (!formData.value.departamentoColegio || !formData.value.provinciaColegio) return []
  return ubigeoData[formData.value.departamentoColegio][formData.value.provinciaColegio] || []
})
const colegiosDisponibles = computed(() => {
  if (!formData.value.distritoColegio) return []
  return colegiosData[formData.value.distritoColegio] || ["COLEGIO NACIONAL MIXTO", "OTRO"]
})
const onDepartamentoColegioChange = () => { formData.value.provinciaColegio = ''; formData.value.distritoColegio = ''; formData.value.nombreColegio = '' }
const onProvinciaColegioChange = () => { formData.value.distritoColegio = ''; formData.value.nombreColegio = '' }
const onDistritoColegioChange = () => { formData.value.nombreColegio = '' }


// --- FUNCIONES PARA FORZAR MAYÚSCULAS Y NÚMEROS ---
const forceLetters = (field: keyof typeof formData.value) => {
  let val = String(formData.value[field]).replace(/[^a-zA-ZáéíóúÁÉÍÓÚñÑ ]/g, '').toUpperCase()
  ;(formData.value[field] as string) = val
}

const forceNumbers = (field: keyof typeof formData.value, maxLength: number) => {
  let val = String(formData.value[field]).replace(/[^0-9]/g, '')
  if (val.length > maxLength) val = val.substring(0, maxLength)
  ;(formData.value[field] as string) = val
}

const forceUppercase = (field: keyof typeof formData.value) => {
  ;(formData.value[field] as string) = String(formData.value[field]).toUpperCase()
}

// --- VALIDACIÓN Y ENVÍO DE DATOS ---
const progressBarWidth = computed(() => `${(currentStep.value / totalSteps) * 100}%`)

const nextStep = async () => { 
  errorMsg.value = '' 

  // VALIDACIONES PASO 1
  if (currentStep.value === 1) {
    if (!formData.value.primerApellido || !formData.value.nombres || !formData.value.correo || !formData.value.ubigeoNacimiento || !formData.value.celular || !formData.value.fechaNacimiento) {
      errorMsg.value = 'Debes llenar todos los campos obligatorios (*)'
      return
    }
    if (formData.value.celular.length < 9) {
      errorMsg.value = 'El número de celular debe tener 9 dígitos'
      return
    }
  } 
  // VALIDACIONES PASO 2
  else if (currentStep.value === 2) {
    if (!formData.value.pais || !formData.value.direccion) {
      errorMsg.value = 'El país y la dirección son obligatorios'
      return
    }
    if (formData.value.pais === 'PERÚ' && (!formData.value.departamento || !formData.value.provincia || !formData.value.distrito)) {
      errorMsg.value = 'Debes seleccionar Departamento, Provincia y Distrito'
      return
    }
  }
  // VALIDACIONES PASO 3
  else if (currentStep.value === 3) {
    if (!formData.value.anioEgreso || !formData.value.nombreColegio) {
      errorMsg.value = 'El año de egreso y el nombre del colegio son obligatorios'
      return
    }
  }
  // VALIDACIONES PASO 4
  else if (currentStep.value === 4) {
    if (!formData.value.madreDocumento || !formData.value.madreNombres || !formData.value.madrePrimerApellido) {
      errorMsg.value = 'Los datos principales de la madre son obligatorios'
      return
    }
    if (formData.value.madreDocumento.length !== 8) {
      errorMsg.value = 'El DNI de la madre debe tener exactamente 8 números'
      return
    }
    if (formData.value.padreDocumento && formData.value.padreDocumento.length !== 8) {
      errorMsg.value = 'El DNI del padre debe tener exactamente 8 números'
      return
    }
  }
  
  // PASO 5: ENVÍO A GOOGLE SHEETS
  if (currentStep.value === 5) {
    if (!formData.value.programaEstudio) {
      errorMsg.value = 'Debes seleccionar un Programa de Estudios'
      return
    }
    if (!formData.value.codigoPago) { // <--- NUEVA VALIDACIÓN
      errorMsg.value = 'El código de pago del voucher es obligatorio'
      return
    }

    isSubmitting.value = true
    try {
      await fetch(scriptURL, {
        method: 'POST',
        headers: { 'Content-Type': 'text/plain;charset=utf-8' },
        body: JSON.stringify(formData.value)
      })
      alert("¡Felicidades! Tu preinscripción fue registrada con éxito.")
      
      // Resetea el formulario al terminar
      window.location.reload() 
      
    } catch (error) {
      console.error(error)
      alert("Hubo un error de conexión. Por favor, intenta nuevamente.")
    } finally {
      isSubmitting.value = false
    }
    return 
  }

  // Si pasa las validaciones y no es el paso 5, avanza
  currentStep.value++ 
}

const prevStep = () => { 
  if (currentStep.value > 1) {
    currentStep.value-- 
    errorMsg.value = '' 
  } 
}
</script>

<style scoped>
.bg-light-gray { background-color: #f1f5f9; }
.text-dark-blue { color: #0f172a; }
.text-red-primary { color: #e11d48; }
.bg-red-primary { background-color: #e11d48; }

/* Estilos del Encabezado */
.form-header {
  background-color: #881337;
  padding: 60px 0;
}
.header-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('data:image/svg+xml,%3Csvg width="60" height="60" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg"%3E%3Cg fill="none" fill-rule="evenodd"%3E%3Cg fill="%23ffffff" fill-opacity="0.05"%3E%3Cpath d="M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z"/%3E%3C/g%3E%3C/g%3E%3C/svg%3E');
  z-index: 1;
}
.header-line {
  width: 40px;
  height: 3px;
  background-color: #e11d48;
  border: none;
  opacity: 1;
}

/* Inputs Modernos */
.modern-input {
  background-color: #f8fafc;
  border: 1px solid #e2e8f0;
  padding: 12px 16px;
  border-radius: 8px;
  color: #334155;
  transition: all 0.3s ease;
}
.modern-input:focus {
  background-color: #ffffff;
  border-color: #e11d48;
  box-shadow: 0 0 0 4px rgba(225, 29, 72, 0.1);
  outline: none;
}

/* Radio Buttons personalizados */
.custom-radio:checked {
  background-color: #e11d48;
  border-color: #e11d48;
}

/* Botones */
.btn-red-primary {
  background-color: #e11d48;
  color: white;
  border: none;
  transition: all 0.2s ease;
}
.btn-red-primary:hover {
  background-color: #be123c;
  color: white;
  transform: translateY(-1px);
}

/* Animación de transición entre pasos */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-enter-from { opacity: 0; transform: translateX(20px); }
.fade-leave-to { opacity: 0; transform: translateX(-20px); }

/* =========================================
   ESTILOS DE LA VENTANA FLOTANTE (MODAL UBIGEO)
   ========================================= */
.custom-modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(15, 23, 42, 0.85); /* Fondo oscuro transparente */
  backdrop-filter: blur(4px); /* Efecto de desenfoque */
  z-index: 9999; /* Esto hace que flote por encima de TODO */
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.custom-modal-content {
  position: relative;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto; /* Por si la pantalla del celular es muy pequeña */
}

.close-modal-btn {
  position: absolute;
  top: -15px;
  right: -15px;
  background: #e11d48; /* Rojo IESTP Ayaviri */
  color: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 10;
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
}

.close-modal-btn:hover {
  background: #be123c;
  transform: scale(1.1);
}

/* Animación de entrada y salida suave */
.fade-modal-enter-active,
.fade-modal-leave-active {
  transition: opacity 0.3s ease;
}
.fade-modal-enter-from,
.fade-modal-leave-to {
  opacity: 0;
}
</style>