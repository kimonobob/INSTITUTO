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
          
          <div class="card shadow-lg border-0 rounded-4 overflow-hidden" v-if="!isSuccess">
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
                    <div class="col-md-6">
                        <label class="form-label text-muted small fw-semibold">DNI del Postulante <span class="text-danger">*</span></label>
                        <input type="text" class="form-control modern-input" v-model="formData.dni" @input="forceNumbers('dni', 8)" placeholder="Ej: 71234567">
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
                     <label class="form-label text-muted small fw-semibold">Año de egreso <span class="text-danger">*</span></label>
                      <input type="number" class="form-control modern-input" v-model="formData.anioEgreso" @input="forceNumbers('anioEgreso', 4)" placeholder="Ej: 2019" min="1950" max="2026">
                    </div>

                    <div class="col-12">
                    <label class="form-label text-muted small fw-semibold">País <span class="text-danger">*</span></label>
                    <select class="form-select modern-input" v-model="formData.paisColegio" @change="onDepartamentoColegioChange">
                        <option value="PERÚ">PERÚ</option>
                        <option value="OTRO">OTRO</option>
                    </select>
                    </div>

                    <div class="col-md-4">
                    <label class="form-label text-muted small fw-semibold">Departamento <span class="text-danger">*</span></label>
                    <select class="form-select modern-input" v-model="formData.departamentoColegio" @change="onDepartamentoColegioChange" :disabled="formData.paisColegio !== 'PERÚ'">
                        <option value="">Seleccione...</option>
                        <option v-for="dep in departamentosColegioDisponibles" :key="dep" :value="dep">{{ dep }}</option>
                    </select>
                    </div>
    
                    <div class="col-md-4">
                    <label class="form-label text-muted small fw-semibold">Provincia <span class="text-danger">*</span></label>
                    <select class="form-select modern-input" v-model="formData.provinciaColegio" @change="onProvinciaColegioChange" :disabled="!formData.departamentoColegio || formData.paisColegio !== 'PERÚ'">
                        <option value="">Seleccione...</option>
                        <option v-for="prov in provinciasColegioDisponibles" :key="prov" :value="prov">{{ prov }}</option>
                    </select>
                    </div>

                    <div class="col-md-4">
                    <label class="form-label text-muted small fw-semibold">Distrito <span class="text-danger">*</span></label>
                    <select class="form-select modern-input" v-model="formData.distritoColegio" @change="onDistritoColegioChange" :disabled="!formData.provinciaColegio || formData.paisColegio !== 'PERÚ'">
                        <option value="">Seleccione...</option>
                        <option v-for="dist in distritosColegioDisponibles" :key="dist" :value="dist">{{ dist }}</option>
                    </select>
                    </div>

                   <div class="col-12">
                    <label class="form-label text-muted small fw-semibold">Nombre de colegio <span class="text-danger">*</span></label>
                    
                    <input 
                        type="text" 
                        class="form-control modern-input" 
                        list="lista-colegios" 
                        v-model="formData.nombreColegio" 
                        @input="buscarCodigoModular"
                        :disabled="!formData.distritoColegio || formData.paisColegio !== 'PERÚ'"
                        placeholder="Escribe para buscar tu colegio..."
                    >
                    
                    <datalist id="lista-colegios">
                        <option v-for="colegio in colegiosDisponibles" :key="colegio.COD_MOD" :value="colegio.CEN_EDU"></option>
                    </datalist>
                    
                    <div v-if="formData.codigoModular" class="mt-2 small text-success fw-bold">
                        <i class="bi bi-check-circle-fill"></i> Código Modular detectado: {{ formData.codigoModular }}
                    </div>
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
  <div class="row g-4">
    
    <div class="col-md-6">
      <label class="form-label text-muted small fw-bold">Lugar de Pago <span class="text-danger">*</span></label>
      <select class="form-select modern-input" v-model="formData.metodoPago" @change="formData.metodoPago === 'No realicé el pago' ? formData.codigoPago = '' : null" style="border-color: #cbd5e1; background-color: #f8fafc;">
        <option value="Caja del Instituto">Caja del Instituto</option>
        <option value="Banco de la Nación">Banco de la Nación</option>
        <option value="No realicé el pago">Aún no realicé el pago</option>
      </select>
    </div>

    <div class="col-md-6" v-if="formData.metodoPago !== 'No realicé el pago'">
      
      <div class="d-flex justify-content-between align-items-end mb-2">
        <label class="form-label text-muted small fw-bold mb-0">Código de Operación / Recibo <span class="text-danger">*</span></label>
        
        <a href="#" class="text-red-primary small text-decoration-none">¿Dónde ubicarlo?</a>
      </div>
      
      <input type="text" class="form-control modern-input" v-model="formData.codigoPago" @input="forceUppercase('codigoPago')" placeholder="Ej: 0012345" style="border-color: #cbd5e1; background-color: #f8fafc;">
    
    </div>
    
  </div>
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
          </div> <div class="card shadow-lg border-0 rounded-4 overflow-hidden p-4 p-md-5 text-center success-animation" v-else>
            <div class="mb-4 d-flex justify-content-center mt-4">
              <div class="rounded-circle bg-success bg-opacity-10 d-flex align-items-center justify-content-center" style="width: 100px; height: 100px;">
                <svg xmlns="http://www.w3.org/2000/svg" width="50" height="50" fill="#198754" class="bi bi-check-lg" viewBox="0 0 16 16">
                  <path d="M12.736 3.97a.733.733 0 0 1 1.047 0c.286.289.29.756.01 1.05L7.88 12.01a.733.733 0 0 1-1.065.02L3.217 8.384a.757.757 0 0 1 0-1.06.733.733 0 0 1 1.047 0l3.052 3.093 5.4-6.425a.247.247 0 0 1 .02-.02Z"/>
                </svg>
              </div>
            </div>
            <h2 class="fw-bold text-dark mb-3">¡Felicidades, diste el primer gran paso!</h2>
            <p class="text-muted mb-5 mx-auto fs-5" style="max-width: 600px;">
              Tu preinscripción al <strong>IESTP Ayaviri</strong> ha sido registrada exitosamente. Prepárate para iniciar tu camino profesional. Te invitamos a estar atento a nuestros canales oficiales para los siguientes pasos.
            </p>
            <div class="mb-4">
              <NuxtLink to="/" class="btn btn-red-primary px-5 py-3 rounded-pill fw-bold shadow-sm" style="font-size: 1.1rem;">
                Volver a la página principal
              </NuxtLink>
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
import { ref, computed, onMounted } from 'vue'

const currentStep = ref(1) 
const totalSteps = 5
const errorMsg = ref('') 
const isSubmitting = ref(false)
const isSuccess = ref(false) // <--- NUEVA VARIABLE PARA LA PANTALLA DE ÉXITO

// TU ENLACE REAL DE GOOGLE SHEETS
const scriptURL = 'https://script.google.com/macros/s/AKfycbwqtz6zU_TNBpQGWyKBtrL708wfs_N3pKVpTV26Y-REehkUHihfGmYceCdvrsRGXpdK3g/exec' 

const formData = ref({
  // Paso 1
  dni: '',
  sexo: 'M', estadoCivil: 'Soltero', primerApellido: '', segundoApellido: '', nombres: '',
  correo: '', ubigeoNacimiento: '', celular: '', fechaNacimiento: '',
  
  // Paso 2 (Residencia)
  pais: 'PERÚ', departamento: '', provincia: '', distrito: '', direccion: '',

  // Paso 3 (Colegio)
  anioEgreso: '', paisColegio: 'PERÚ', departamentoColegio: '', provinciaColegio: '',
  distritoColegio: '', nombreColegio: '', codigoModular: '',

  // Paso 4
  madreDocumento: '', madreNombres: '', madrePrimerApellido: '', madreSegundoApellido: '',
  padreDocumento: '', padreNombres: '', padrePrimerApellido: '', padreSegundoApellido: '',
  
  // Paso 5
  modalidad: 'EXAMEN GENERAL', programaEstudio: '', tipoCertificado: '', codigoCertificado: '', codigoPago: '',metodoPago: 'Caja del Instituto'
})

// --- CONSTANTES ---
const modalidades = ['ORDINARIO', 'EXONERADO (PRIMEROS PUESTOS)', 'EXTRAORDINARIO']
const programasEstudio = ['Contabilidad', 'Enfermería Técnica', 'Producción Agropecuaria', 'Industrias Alimentarias', 'Arquitectura de Plataformas y Servicios de Tecnologías de Información']
const tiposCertificado = ['Certificado de Estudios (Amarillo)', 'Certificado de Estudios (Blanco)', 'Constancia de Logros de Aprendizaje (CLA)']

// --- LÓGICA DE LA VENTANA FLOTANTE (UBIGEO) ---
const showUbigeoModal = ref(false)
const activeDniTab = ref('azul') 

const dniImages: Record<string, string> = {
  azul: '/images/admision/dnia.jpg',
  electronico: '/images/admision/dnie.jpg',
  amarillo: '/images/admision/dniam.jpg'
}

const openUbigeoModal = () => {
  activeDniTab.value = 'azul' 
  showUbigeoModal.value = true
}
const closeUbigeoModal = () => { showUbigeoModal.value = false }

// --- LÓGICA DE LA VENTANA FLOTANTE (CERTIFICADOS) ---
const showCertificadoModal = ref(false)
const activeCertificadoTab = ref('amarillo') 

const certificadoImages: Record<string, string> = {
  amarillo: '/images/admision/certia.jpg',
  blanco: '/images/admision/certib.jpg',
  constancia: '/images/admision/constanciae.jpg'
}

const openCertificadoModal = () => {
  activeCertificadoTab.value = 'amarillo' 
  showCertificadoModal.value = true
}
const closeCertificadoModal = () => { showCertificadoModal.value = false }

// ==============================================================
// BASE DE DATOS MAESTRA (PARA RESIDENCIA Y COLEGIOS)
// ==============================================================
const colegiosDatabase = ref<any[]>([])

onMounted(async () => {
  try {
    const respuesta = await fetch('/Documentos/IEsecundaria.json')
    colegiosDatabase.value = await respuesta.json()
    console.log("¡Base de datos nacional cargada exitosamente!")
  } catch (error) {
    console.error("Error al cargar IEsecundaria.json:", error)
  }
})

// Obtenemos todos los departamentos del Perú de forma única
const departamentosNacionales = computed(() => {
  if (colegiosDatabase.value.length === 0) return []
  const departamentos = colegiosDatabase.value.map(item => item.D_DPTO)
  return [...new Set(departamentos)].sort()
})

// ==============================================================
// LÓGICA DE CASCADA PARA EL PASO 2 (RESIDENCIA)
// ==============================================================
const departamentosDisponibles = computed(() => departamentosNacionales.value)

const provinciasDisponibles = computed(() => {
  if (!formData.value.departamento) return []
  const provincias = colegiosDatabase.value
    .filter(item => item.D_DPTO === formData.value.departamento)
    .map(item => item.D_PROV)
  return [...new Set(provincias)].sort()
})

const distritosDisponibles = computed(() => {
  if (!formData.value.provincia) return []
  const distritos = colegiosDatabase.value
    .filter(item => 
      item.D_DPTO === formData.value.departamento &&
      item.D_PROV === formData.value.provincia
    )
    .map(item => item.D_DIST)
  return [...new Set(distritos)].sort()
})

const onDepartamentoChange = () => { formData.value.provincia = ''; formData.value.distrito = '' }
const onProvinciaChange = () => { formData.value.distrito = '' }


// ==============================================================
// LÓGICA DE CASCADA PARA EL PASO 3 (COLEGIOS)
// ==============================================================
const departamentosColegioDisponibles = computed(() => departamentosNacionales.value)

const provinciasColegioDisponibles = computed(() => {
  if (!formData.value.departamentoColegio) return []
  const provincias = colegiosDatabase.value
    .filter(item => item.D_DPTO === formData.value.departamentoColegio)
    .map(item => item.D_PROV)
  return [...new Set(provincias)].sort()
})

const distritosColegioDisponibles = computed(() => {
  if (!formData.value.provinciaColegio) return []
  const distritos = colegiosDatabase.value
    .filter(item => 
      item.D_DPTO === formData.value.departamentoColegio &&
      item.D_PROV === formData.value.provinciaColegio
    )
    .map(item => item.D_DIST)
  return [...new Set(distritos)].sort()
})

const colegiosDisponibles = computed(() => {
  if (!formData.value.distritoColegio) return []
  const colegiosFiltrados = colegiosDatabase.value
    .filter(item => 
      item.D_DPTO === formData.value.departamentoColegio &&
      item.D_PROV === formData.value.provinciaColegio && 
      item.D_DIST === formData.value.distritoColegio
    )
    .sort((a, b) => a.CEN_EDU.localeCompare(b.CEN_EDU))
  return colegiosFiltrados
})

const onDepartamentoColegioChange = () => { formData.value.provinciaColegio = ''; formData.value.distritoColegio = ''; formData.value.nombreColegio = '' }
const onProvinciaColegioChange = () => { formData.value.distritoColegio = ''; formData.value.nombreColegio = '' }
const onDistritoColegioChange = () => { formData.value.nombreColegio = '' }


// Función que se ejecuta cada vez que el postulante escribe o selecciona un colegio
const buscarCodigoModular = () => {
  // 1. Convertimos a mayúsculas
  formData.value.nombreColegio = String(formData.value.nombreColegio).toUpperCase()

  // 2. Buscamos el colegio exacto en la lista del distrito
  const colegioEncontrado = colegiosDisponibles.value.find(
    (c) => c.CEN_EDU === formData.value.nombreColegio
  )

  // 3. Separamos los datos: El código se va a su variable, el nombre se queda en la suya
  if (colegioEncontrado) {
    formData.value.codigoModular = colegioEncontrado.COD_MOD
  } else {
    formData.value.codigoModular = ''
  }
}

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
    // 👇 Se agregó !formData.value.dni para que sea obligatorio no dejarlo vacío
    if (!formData.value.dni || !formData.value.primerApellido || !formData.value.nombres || !formData.value.correo || !formData.value.ubigeoNacimiento || !formData.value.celular || !formData.value.fechaNacimiento) {
      errorMsg.value = 'Debes llenar todos los campos obligatorios (*)'
      return
    }
    
    if (formData.value.dni.length !== 8) {
      errorMsg.value = 'El DNI debe tener exactamente 8 números'
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
    // 👇 Eliminé la validación del padre porque ya no existe en tu formulario
  }
  
 // PASO 5: ENVÍO A GOOGLE SHEETS
  if (currentStep.value === 5) {
    if (!formData.value.programaEstudio) {
      errorMsg.value = 'Debes seleccionar un Programa de Estudios'
      return
    }

    isSubmitting.value = true
    try {
      await fetch(scriptURL, {
        method: 'POST',
        headers: { 'Content-Type': 'text/plain;charset=utf-8' },
        body: JSON.stringify(formData.value)
      })
      
      // 👇 Activamos la pantalla de éxito moderna y subimos la vista arriba
      isSuccess.value = true 
      window.scrollTo({ top: 0, behavior: 'smooth' })
      
    } catch (error) {
      console.error(error)
      errorMsg.value = "Hubo un error de conexión. Por favor, revisa tu internet e intenta nuevamente."
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

.success-animation {
  animation: slideUpFade 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}

@keyframes slideUpFade {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>