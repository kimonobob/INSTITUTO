<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-one title="Libro de Reclamaciones" subtitle="Atención al Usuario" />
      <!-- breadcrumb area end -->

      <!-- Libro de Reclamaciones start -->
      <section class="tp-course-requrement-area grey-bg pt-100 pb-80">
        <div class="container">
          <div class="row">
            <!-- MAIN -->
            <div class="col-lg-9">
              <div class="tp-course-requrement-wrapper book-wrap">

                <!-- Header moderno -->
                <div class="book-hero">
                  <div class="book-hero-left">
                    <span class="book-kicker">Canal oficial</span>
                    <h3 class="tp-course-requrement-title book-title">Libro de Reclamaciones</h3>
                    <p class="book-subtitle">
                      Registra tu reclamo o queja de manera formal. Tu solicitud será atendida conforme a los plazos y
                      procedimientos institucionales.
                    </p>
                  </div>

                  <div class="book-hero-right">
                    <div class="book-pills">
                      <span class="book-pill">Formulario digital</span>
                      <span class="book-pill book-pill--soft">Respuesta institucional</span>
                    </div>

                    <div class="book-tip">
                      <span class="book-tip-ico" aria-hidden="true">i</span>
                      <p class="book-tip-text">
                        Completa la información de forma clara para agilizar la atención.
                      </p>
                    </div>
                  </div>
                </div>

                <!-- Form Card -->
                <div class="book-card">
                  <div class="book-card-head">
                    <h4 class="book-card-title">Registro de reclamo / queja</h4>
                    <p class="book-card-subtitle">
                      Los campos marcados con <span class="req">*</span> son obligatorios.
                    </p>
                  </div>

                  <form class="book-form" @submit.prevent="onSubmit" novalidate>
                    <!-- Datos del solicitante -->
                    <div class="book-section">
                      <h5 class="book-section-title">1) Datos del usuario</h5>

                      <div class="book-grid">
                        <div class="field">
                          <label for="fullName">Nombres y apellidos <span class="req">*</span></label>
                          <input
                            id="fullName"
                            v-model.trim="form.fullName"
                            type="text"
                            placeholder="Ej. Juan Carlos Quispe"
                            :class="{ invalid: touched.fullName && !validFullName }"
                            @blur="touched.fullName = true"
                            autocomplete="name"
                            required
                          />
                          <small v-if="touched.fullName && !validFullName" class="error">
                            Ingresa tu nombre completo.
                          </small>
                        </div>

                        <div class="field">
                          <label for="docType">Tipo de documento <span class="req">*</span></label>
                          <select
                            id="docType"
                            v-model="form.docType"
                            :class="{ invalid: touched.docType && !validDocType }"
                            @blur="touched.docType = true"
                            required
                          >
                            <option value="" disabled>Selecciona</option>
                            <option value="DNI">DNI</option>
                            <option value="CE">Carné de Extranjería</option>
                            <option value="Pasaporte">Pasaporte</option>
                            <option value="Otro">Otro</option>
                          </select>
                          <small v-if="touched.docType && !validDocType" class="error">
                            Selecciona el tipo de documento.
                          </small>
                        </div>

                        <div class="field">
                          <label for="docNumber">N° de documento <span class="req">*</span></label>
                          <input
                            id="docNumber"
                            v-model.trim="form.docNumber"
                            type="text"
                            inputmode="numeric"
                            placeholder="Ej. 12345678"
                            :class="{ invalid: touched.docNumber && !validDocNumber }"
                            @blur="touched.docNumber = true"
                            required
                          />
                          <small v-if="touched.docNumber && !validDocNumber" class="error">
                            Ingresa un número de documento válido.
                          </small>
                        </div>

                        <div class="field">
                          <label for="phone">Celular / WhatsApp <span class="req">*</span></label>
                          <input
                            id="phone"
                            v-model.trim="form.phone"
                            type="tel"
                            placeholder="Ej. 999 888 777"
                            :class="{ invalid: touched.phone && !validPhone }"
                            @blur="touched.phone = true"
                            autocomplete="tel"
                            required
                          />
                          <small v-if="touched.phone && !validPhone" class="error">
                            Ingresa un celular válido.
                          </small>
                        </div>

                        <div class="field">
                          <label for="email">Correo electrónico <span class="req">*</span></label>
                          <input
                            id="email"
                            v-model.trim="form.email"
                            type="email"
                            placeholder="Ej. correo@dominio.com"
                            :class="{ invalid: touched.email && !validEmail }"
                            @blur="touched.email = true"
                            autocomplete="email"
                            required
                          />
                          <small v-if="touched.email && !validEmail" class="error">
                            Ingresa un correo válido.
                          </small>
                        </div>

                        <div class="field">
                          <label for="address">Dirección (opcional)</label>
                          <input
                            id="address"
                            v-model.trim="form.address"
                            type="text"
                            placeholder="Ej. Jr. ... / Av. ..."
                            autocomplete="street-address"
                          />
                        </div>
                      </div>
                    </div>

                    <!-- Datos del hecho -->
                    <div class="book-section">
                      <h5 class="book-section-title">2) Detalle del reclamo</h5>

                      <div class="book-grid">
                        <div class="field">
                          <label for="type">Tipo <span class="req">*</span></label>
                          <select
                            id="type"
                            v-model="form.type"
                            :class="{ invalid: touched.type && !validType }"
                            @blur="touched.type = true"
                            required
                          >
                            <option value="" disabled>Selecciona</option>
                            <option value="Reclamo">Reclamo</option>
                            <option value="Queja">Queja</option>
                          </select>
                          <small v-if="touched.type && !validType" class="error">
                            Selecciona el tipo de registro.
                          </small>
                        </div>

                        <div class="field">
                          <label for="area">Área relacionada <span class="req">*</span></label>
                          <select
                            id="area"
                            v-model="form.area"
                            :class="{ invalid: touched.area && !validArea }"
                            @blur="touched.area = true"
                            required
                          >
                            <option value="" disabled>Selecciona</option>
                            <option value="Admisión">Admisión</option>
                            <option value="Secretaría Académica">Secretaría Académica</option>
                            <option value="Tesorería / Caja">Tesorería / Caja</option>
                            <option value="Trámite documentario">Trámite documentario</option>
                            <option value="Bienestar estudiantil">Bienestar estudiantil</option>
                            <option value="Otro">Otro</option>
                          </select>
                          <small v-if="touched.area && !validArea" class="error">
                            Selecciona el área relacionada.
                          </small>
                        </div>

                        <div class="field">
                          <label for="date">Fecha del hecho (opcional)</label>
                          <input id="date" v-model="form.date" type="date" />
                        </div>

                        <div class="field">
                          <label for="channel">Preferencia de respuesta</label>
                          <select id="channel" v-model="form.responseChannel">
                            <option value="Correo">Correo</option>
                            <option value="WhatsApp">WhatsApp</option>
                            <option value="Llamada">Llamada</option>
                          </select>
                        </div>

                        <div class="field full">
                          <label for="detail">Detalle <span class="req">*</span></label>
                          <textarea
                            id="detail"
                            v-model.trim="form.detail"
                            rows="5"
                            placeholder="Describe el hecho: qué ocurrió, cuándo, dónde y a quiénes involucra."
                            :class="{ invalid: touched.detail && !validDetail }"
                            @blur="touched.detail = true"
                            required
                          ></textarea>
                          <small v-if="touched.detail && !validDetail" class="error">
                            Describe el hecho (mínimo 20 caracteres).
                          </small>
                        </div>

                        <div class="field full">
                          <label for="request">Pedido del usuario <span class="req">*</span></label>
                          <textarea
                            id="request"
                            v-model.trim="form.request"
                            rows="4"
                            placeholder="Indica lo que solicitas como solución o atención."
                            :class="{ invalid: touched.request && !validRequest }"
                            @blur="touched.request = true"
                            required
                          ></textarea>
                          <small v-if="touched.request && !validRequest" class="error">
                            Indica tu solicitud (mínimo 10 caracteres).
                          </small>
                        </div>
                      </div>
                    </div>

                    <!-- Consent -->
                    <div class="book-section">
                      <h5 class="book-section-title">3) Confirmación</h5>

                      <label class="consent">
                        <input
                          type="checkbox"
                          v-model="form.consent"
                          @change="touched.consent = true"
                        />
                        <span>
                          Declaro que la información proporcionada es verdadera y autorizo el uso de mis datos para la
                          atención del presente reclamo/queja. <span class="req">*</span>
                        </span>
                      </label>
                      <small v-if="touched.consent && !validConsent" class="error">
                        Debes aceptar para registrar el reclamo/queja.
                      </small>
                    </div>

                    <!-- Actions -->
                    <div class="book-actions">
                      <button class="btn-primary" type="submit" :disabled="loading">
                        <span v-if="!loading">Registrar</span>
                        <span v-else>Enviando...</span>
                      </button>

                      <p class="helper">
                        Recibirás una confirmación por el medio seleccionado. Conserva tu constancia.
                      </p>

                      <div v-if="status === 'success'" class="alert success" role="status">
                        ¡Registro enviado! Tu solicitud fue registrada correctamente.
                      </div>
                      <div v-if="status === 'error'" class="alert error" role="alert">
                        Ocurrió un error al enviar. Inténtalo nuevamente.
                      </div>
                    </div>
                  </form>
                </div>

              </div>
            </div>

            <!-- SIDEBAR -->
            <div class="col-lg-3">
              <div class="tp-course-requrement-widget-box">

                <div class="tp-course-requrement-widget mb-30">
                  <div class="tp-course-requrement-widget-content">
                    <nuxt-link href="/documentos">Documentos</nuxt-link>
                    <nuxt-link href="/tupa">TUPA 2024</nuxt-link>
                    <nuxt-link href="/contacto">Contacto</nuxt-link>
                    <nuxt-link href="/faq">Preguntas frecuentes</nuxt-link>
                  </div>
                </div>

                <div class="tp-course-requrement-widget-btn mb-30">
                  <nuxt-link class="tp-btn btn-1 w-100 text-center" href="/university-request-info">
                    Solicitar información
                  </nuxt-link>
                  <nuxt-link class="tp-btn btn-2 w-100 text-center" href="/university-apply">
                    Postular ahora
                  </nuxt-link>
                </div>

                <div class="tp-course-requrement-widget-contact mb-30">
                  <h4 class="tp-course-requrement-widget-contact-title">Contacto</h4>
                  <p>Ayaviri, Melgar – Puno</p>
                  <a href="mailto:informes@iestpayaviri.edu.pe"><span><svg-email-one /></span> informes@iestpayaviri.edu.pe</a>
                  <a href="tel:+51000000000"><span><svg-phone /></span> +51 000 000 000</a>
                </div>

                <div class="tp-course-requrement-widget-faq">
                  <h4 class="tp-course-requrement-widget-faq-title">¿Necesitas ayuda?</h4>
                  <p>Revisa nuestras <nuxt-link href="/faq">Preguntas frecuentes</nuxt-link></p>
                  <div class="tp-course-requrement-widget-faq-thumb">
                    <img src="/images/history/undergraduate/course-contact-bg.png" alt="">
                  </div>
                </div>

              </div>
            </div>

          </div>
        </div>
      </section>
      <!-- Libro de Reclamaciones end -->

    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { computed, reactive, ref } from "vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "Libro de Reclamaciones - IESTP" });

type FormState = {
  fullName: string;
  docType: "DNI" | "CE" | "Pasaporte" | "Otro" | "";
  docNumber: string;
  phone: string;
  email: string;
  address: string;
  type: "Reclamo" | "Queja" | "";
  area: string;
  date: string;
  responseChannel: "Correo" | "WhatsApp" | "Llamada";
  detail: string;
  request: string;
  consent: boolean;
};

const form = reactive<FormState>({
  fullName: "",
  docType: "",
  docNumber: "",
  phone: "",
  email: "",
  address: "",
  type: "",
  area: "",
  date: "",
  responseChannel: "Correo",
  detail: "",
  request: "",
  consent: false,
});

const touched = reactive({
  fullName: false,
  docType: false,
  docNumber: false,
  phone: false,
  email: false,
  type: false,
  area: false,
  detail: false,
  request: false,
  consent: false,
});

const loading = ref(false);
const status = ref<"idle" | "success" | "error">("idle");

/** Validadores */
const validFullName = computed(() => form.fullName.length >= 6 && form.fullName.includes(" "));
const validDocType = computed(() => !!form.docType);
const validDocNumber = computed(() => form.docNumber.trim().length >= 6);
const validPhone = computed(() => form.phone.replace(/\D/g, "").length >= 9);
const validEmail = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email));
const validType = computed(() => !!form.type);
const validArea = computed(() => !!form.area);
const validDetail = computed(() => form.detail.trim().length >= 20);
const validRequest = computed(() => form.request.trim().length >= 10);
const validConsent = computed(() => form.consent);

const isValid = computed(() =>
  validFullName.value &&
  validDocType.value &&
  validDocNumber.value &&
  validPhone.value &&
  validEmail.value &&
  validType.value &&
  validArea.value &&
  validDetail.value &&
  validRequest.value &&
  validConsent.value
);

function touchAll() {
  Object.keys(touched).forEach((k) => ((touched as any)[k] = true));
}

async function onSubmit() {
  status.value = "idle";
  touchAll();
  if (!isValid.value) return;

  try {
    loading.value = true;

    /**
     * ✅ Aquí conectas tu backend luego:
     * await $fetch("/api/libro-reclamaciones", { method: "POST", body: form })
     */
    await new Promise((r) => setTimeout(r, 650));

    status.value = "success";

    // Reset
    form.fullName = "";
    form.docType = "";
    form.docNumber = "";
    form.phone = "";
    form.email = "";
    form.address = "";
    form.type = "";
    form.area = "";
    form.date = "";
    form.responseChannel = "Correo";
    form.detail = "";
    form.request = "";
    form.consent = false;

    Object.keys(touched).forEach((k) => ((touched as any)[k] = false));
  } catch (e) {
    status.value = "error";
  } finally {
    loading.value = false;
  }
}
</script>

<style scoped>
/* ===== Libro de Reclamaciones - Estilo moderno institucional ===== */
.book-wrap {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* Hero */
.book-hero {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  gap: 16px;
  padding: 18px;
  border-radius: 22px;
  border: 1px solid var(--line);
  background: linear-gradient(180deg, rgba(255,255,255,0.92), rgba(255,255,255,0.70));
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  position: relative;
  overflow: hidden;
  margin-bottom: 14px;
}

.book-hero::after {
  content: "";
  position: absolute;
  top: -60px;
  right: -60px;
  width: 240px;
  height: 240px;
  border-radius: 50%;
  background: rgba(177, 4, 14, 0.10);
}

.book-kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.book-title {
  margin: 8px 0 6px;
  font-size: 34px;
  font-weight: 950;
  letter-spacing: -0.03em;
  color: var(--text);
}

.book-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
  max-width: 66ch;
}

.book-hero-right {
  display: grid;
  gap: 10px;
  align-content: start;
}

.book-pills {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.book-pill {
  display: inline-flex;
  align-items: center;
  padding: 8px 12px;
  border-radius: 999px;
  border: 1px solid rgba(15, 23, 42, 0.12);
  background: rgba(2, 6, 23, 0.03);
  color: var(--text);
  font-weight: 900;
  font-size: 12px;
}

.book-pill--soft {
  background: rgba(177, 4, 14, 0.08);
  border-color: rgba(177, 4, 14, 0.18);
  color: var(--brand);
}

.book-tip {
  display: grid;
  grid-template-columns: 34px 1fr;
  gap: 10px;
  padding: 12px;
  border-radius: 18px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(2, 6, 23, 0.02);
}

.book-tip-ico {
  width: 34px;
  height: 34px;
  border-radius: 12px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--soft);
  color: var(--brand);
  font-weight: 950;
}

.book-tip-text {
  margin: 0;
  color: rgba(15, 23, 42, 0.75);
  font-size: 13px;
  line-height: 1.35;
}

/* Card */
.book-card {
  border-radius: 22px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  overflow: hidden;
}

.book-card-head {
  padding: 16px;
  border-bottom: 1px solid rgba(15, 23, 42, 0.10);
  background: linear-gradient(135deg, rgba(177, 4, 14, 0.10), rgba(2, 6, 23, 0.02));
}

.book-card-title {
  margin: 0 0 6px;
  font-size: 16px;
  font-weight: 950;
  color: var(--text);
}

.book-card-subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 13px;
}

.req {
  color: var(--brand);
  font-weight: 950;
}

.book-form {
  padding: 16px;
}

.book-section {
  padding: 14px 0;
  border-bottom: 1px solid rgba(15, 23, 42, 0.08);
}

.book-section:last-child {
  border-bottom: none;
}

.book-section-title {
  margin: 0 0 12px;
  font-size: 14px;
  font-weight: 950;
  color: var(--text);
}

.book-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 14px;
}

.field label {
  display: block;
  margin-bottom: 8px;
  font-weight: 850;
  font-size: 13px;
  color: var(--text);
}

.field input,
.field select,
.field textarea {
  width: 100%;
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.12);
  background: rgba(255, 255, 255, 0.96);
  padding: 12px 12px;
  outline: none;
  transition: box-shadow 0.15s ease, border-color 0.15s ease;
  font-size: 14px;
  color: var(--text);
}

.field input:focus,
.field select:focus,
.field textarea:focus {
  border-color: rgba(177, 4, 14, 0.35);
  box-shadow: 0 0 0 4px rgba(177, 4, 14, 0.12);
}

.field textarea {
  resize: vertical;
  min-height: 110px;
}

.field.full {
  grid-column: 1 / -1;
}

.invalid {
  border-color: rgba(220, 38, 38, 0.55) !important;
  box-shadow: 0 0 0 4px rgba(220, 38, 38, 0.10) !important;
}

.error {
  display: block;
  margin-top: 6px;
  color: rgba(220, 38, 38, 0.95);
  font-size: 12px;
  font-weight: 750;
}

/* Consent */
.consent {
  display: grid;
  grid-template-columns: 18px 1fr;
  gap: 10px;
  align-items: start;
  padding: 12px;
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(2, 6, 23, 0.03);
}

.consent input {
  width: 18px;
  height: 18px;
  margin-top: 2px;
}

/* Actions */
.book-actions {
  margin-top: 14px;
  display: grid;
  gap: 10px;
}

.btn-primary {
  width: fit-content;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 12px 16px;
  border-radius: 999px;
  background: linear-gradient(135deg, var(--brand), var(--brand2));
  color: #fff;
  border: 1px solid rgba(177, 4, 14, 0.35);
  font-weight: 950;
  font-size: 13px;
  letter-spacing: 0.01em;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}

.btn-primary:hover {
  transform: translateY(-1px);
  box-shadow: 0 14px 30px rgba(177, 4, 14, 0.22);
}

.btn-primary:disabled {
  opacity: 0.7;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}

.helper {
  margin: 0;
  color: var(--muted);
  font-size: 13px;
}

/* Alerts */
.alert {
  margin-top: 10px;
  padding: 12px 14px;
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  font-weight: 850;
  font-size: 13px;
}

.alert.success {
  background: rgba(16, 185, 129, 0.10);
  border-color: rgba(16, 185, 129, 0.25);
  color: rgba(15, 118, 110, 1);
}

.alert.error {
  background: rgba(239, 68, 68, 0.10);
  border-color: rgba(239, 68, 68, 0.25);
  color: rgba(185, 28, 28, 1);
}

@media (max-width: 991px) {
  .book-hero {
    grid-template-columns: 1fr;
  }
  .book-title {
    font-size: 28px;
  }
  .book-grid {
    grid-template-columns: 1fr;
  }
}
</style>
