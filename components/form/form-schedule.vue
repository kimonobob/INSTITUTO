<template>
  <section class="info-form-area grey-bg pt-110 pb-110">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-10">
          <div class="info-form-wrap">

            <!-- Header -->
            <div class="info-form-head">
              <span class="kicker">Atención al postulante</span>
              <h2 class="title">Solicitar información</h2>
              <p class="subtitle">
                Completa el formulario y te responderemos a la brevedad con los detalles del proceso, requisitos y costos.
              </p>
            </div>

            <form class="info-form" @submit.prevent="onSubmit" novalidate>
              <div class="grid">

                <div class="field">
                  <label for="fullName">Nombres y apellidos</label>
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
                  <label for="dni">DNI (opcional)</label>
                  <input
                    id="dni"
                    v-model.trim="form.dni"
                    type="text"
                    inputmode="numeric"
                    placeholder="8 dígitos"
                    maxlength="8"
                    :class="{ invalid: touched.dni && !validDni }"
                    @blur="touched.dni = true"
                    autocomplete="off"
                  />
                  <small v-if="touched.dni && !validDni" class="error">
                    Si lo ingresas, debe tener 8 dígitos.
                  </small>
                </div>

                <div class="field">
                  <label for="phone">Celular / WhatsApp</label>
                  <input
                    id="phone"
                    v-model.trim="form.phone"
                    type="tel"
                    inputmode="tel"
                    placeholder="Ej. 999 888 777"
                    :class="{ invalid: touched.phone && !validPhone }"
                    @blur="touched.phone = true"
                    autocomplete="tel"
                    required
                  />
                  <small v-if="touched.phone && !validPhone" class="error">
                    Ingresa un número válido (9 a 12 dígitos).
                  </small>
                </div>

                <div class="field">
                  <label for="email">Correo electrónico</label>
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
                  <label for="program">Programa de estudio</label>
                  <select
                    id="program"
                    v-model="form.program"
                    :class="{ invalid: touched.program && !validProgram }"
                    @blur="touched.program = true"
                    required
                  >
                    <option value="" disabled>Selecciona una opción</option>
                    <option v-for="p in programs" :key="p" :value="p">{{ p }}</option>
                  </select>
                  <small v-if="touched.program && !validProgram" class="error">
                    Selecciona el programa de tu interés.
                  </small>
                </div>

                <div class="field">
                  <label for="shift">Turno</label>
                  <select id="shift" v-model="form.shift">
                    <option value="">Seleccionar (opcional)</option>
                    <option value="Mañana">Mañana</option>
                    <option value="Tarde">Tarde</option>
                    <option value="Noche">Noche</option>
                  </select>
                </div>

                <div class="field">
                  <label for="modality">Modalidad</label>
                  <select id="modality" v-model="form.modality">
                    <option value="">Seleccionar (opcional)</option>
                    <option value="Ordinario">Ordinario</option>
                    <option value="Traslado">Traslado</option>
                    <option value="Exoneración / Modalidades">Exoneración / Modalidades</option>
                  </select>
                </div>

                <div class="field">
                  <label for="contact">Preferencia de contacto</label>
                  <select id="contact" v-model="form.contactPreference">
                    <option value="WhatsApp">WhatsApp</option>
                    <option value="Llamada">Llamada</option>
                    <option value="Correo">Correo</option>
                  </select>
                </div>

                <div class="field full">
                  <label for="message">Consulta</label>
                  <textarea
                    id="message"
                    v-model.trim="form.message"
                    rows="4"
                    placeholder="Escribe tu consulta (requisitos, costos, fechas, convalidaciones, etc.)"
                    :class="{ invalid: touched.message && !validMessage }"
                    @blur="touched.message = true"
                    required
                  ></textarea>
                  <small v-if="touched.message && !validMessage" class="error">
                    Escribe tu consulta (mínimo 10 caracteres).
                  </small>
                </div>

                <div class="field full">
                  <label class="consent">
                    <input
                      type="checkbox"
                      v-model="form.consent"
                      :class="{ invalid: touched.consent && !validConsent }"
                      @change="touched.consent = true"
                    />
                    <span>
                      Autorizo el uso de mis datos para fines de contacto y atención de mi solicitud.
                    </span>
                  </label>
                  <small v-if="touched.consent && !validConsent" class="error">
                    Debes aceptar para enviar la solicitud.
                  </small>
                </div>

              </div>

              <!-- Footer -->
              <div class="form-actions">
                <button class="btn-primary" type="submit" :disabled="loading">
                  <span v-if="!loading">Enviar solicitud</span>
                  <span v-else>Enviando...</span>
                </button>

                <p class="helper">
                  Te responderemos en horario de atención. También puedes escribirnos por WhatsApp.
                </p>
              </div>

              <div v-if="status === 'success'" class="alert success" role="status">
                ¡Listo! Tu solicitud fue enviada. En breve nos pondremos en contacto.
              </div>
              <div v-if="status === 'error'" class="alert error" role="alert">
                Ocurrió un error al enviar. Inténtalo nuevamente.
              </div>
            </form>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed, reactive, ref } from "vue";

type FormState = {
  fullName: string;
  dni: string;
  phone: string;
  email: string;
  program: string;
  shift: string;
  modality: string;
  contactPreference: "WhatsApp" | "Llamada" | "Correo";
  message: string;
  consent: boolean;
};

const programs = [
  "Contabilidad",
  "Computación e Informática",
  "Enfermería Técnica",
  "Administración",
  "Otro"
];

const form = reactive<FormState>({
  fullName: "",
  dni: "",
  phone: "",
  email: "",
  program: "",
  shift: "",
  modality: "",
  contactPreference: "WhatsApp",
  message: "",
  consent: false,
});

const touched = reactive({
  fullName: false,
  dni: false,
  phone: false,
  email: false,
  program: false,
  message: false,
  consent: false,
});

const loading = ref(false);
const status = ref<"idle" | "success" | "error">("idle");

/** Validators */
const validFullName = computed(() => form.fullName.length >= 6 && form.fullName.includes(" "));
const validDni = computed(() => form.dni === "" || /^[0-9]{8}$/.test(form.dni));
const validPhone = computed(() => /^[0-9\s+()-]{9,16}$/.test(form.phone) && (form.phone.replace(/\D/g, "").length >= 9));
const validEmail = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email));
const validProgram = computed(() => !!form.program);
const validMessage = computed(() => form.message.length >= 10);
const validConsent = computed(() => form.consent);

const isValid = computed(
  () =>
    validFullName.value &&
    validDni.value &&
    validPhone.value &&
    validEmail.value &&
    validProgram.value &&
    validMessage.value &&
    validConsent.value
);

function touchAll() {
  touched.fullName = true;
  touched.dni = true;
  touched.phone = true;
  touched.email = true;
  touched.program = true;
  touched.message = true;
  touched.consent = true;
}

async function onSubmit() {
  status.value = "idle";
  touchAll();

  if (!isValid.value) return;

  try {
    loading.value = true;

    /**
     * Conecta aquí tu backend:
     * await $fetch("/api/solicitud-info", { method: "POST", body: form })
     */

    // Simulación de envío
    await new Promise((r) => setTimeout(r, 650));

    status.value = "success";

    // Reset
    form.fullName = "";
    form.dni = "";
    form.phone = "";
    form.email = "";
    form.program = "";
    form.shift = "";
    form.modality = "";
    form.contactPreference = "WhatsApp";
    form.message = "";
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
.info-form-wrap {
  --brand: #b1040e;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);

  border-radius: 22px;
  border: 1px solid var(--line);
  background: linear-gradient(180deg, rgba(255,255,255,0.95), rgba(255,255,255,0.75));
  box-shadow: 0 16px 50px rgba(2, 6, 23, 0.08);
  overflow: hidden;
}

.info-form-head {
  padding: 22px 22px 10px;
}

.kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.title {
  margin: 8px 0 6px;
  font-size: 32px;
  letter-spacing: -0.02em;
  font-weight: 950;
  color: var(--text);
}

.subtitle {
  margin: 0;
  color: var(--muted);
  font-size: 15px;
  max-width: 62ch;
}

.info-form {
  padding: 0 22px 22px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 14px;
  margin-top: 14px;
}

.field label {
  display: block;
  margin-bottom: 8px;
  font-weight: 800;
  font-size: 13px;
  color: var(--text);
}

.field input,
.field select,
.field textarea {
  width: 100%;
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.12);
  background: rgba(255, 255, 255, 0.95);
  padding: 12px 12px;
  outline: none;
  transition: box-shadow 0.15s ease, border-color 0.15s ease, transform 0.05s ease;
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
  font-weight: 700;
}

/* Consent */
.consent {
  display: grid;
  grid-template-columns: 18px 1fr;
  gap: 10px;
  align-items: start;
  padding: 12px 12px;
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
.form-actions {
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
  background: var(--brand);
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
  margin-top: 12px;
  padding: 12px 14px;
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  font-weight: 800;
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

/* Responsive */
@media (max-width: 991px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .title {
    font-size: 26px;
  }
}
</style>
