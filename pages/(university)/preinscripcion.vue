<template>
  <div>
    <nuxt-layout name="layout-eight">

      <!-- breadcrumb area start -->
      <breadcrumb-inscription title="Preinscripción" subtitle="Admisión" :admission="true" />
      <!-- breadcrumb area end -->

      <guiaexamen />
      
      <div id="programas-estudio">
        <program-two />
      </div>
      
      <counter-four />
      <faq-area />
    </nuxt-layout>
  </div>
</template>

<script setup lang="ts">
import { computed, reactive, ref } from "vue";
import Guiaexamen from "../../components/cart/guiaexamen.vue";

definePageMeta({ layout: false });
useSeoMeta({ title: "Preinscripción - Admisión" });

type PreForm = {
  fullName: string;
  docType: "DNI" | "CE" | "Pasaporte" | "Otro" | "";
  docNumber: string;
  birthDate: string;
  phone: string;
  email: string;
  address: string;
  program: string;
  modality: string;
  message: string;
  consent: boolean;
};

const form = reactive<PreForm>({
  fullName: "",
  docType: "",
  docNumber: "",
  birthDate: "",
  phone: "",
  email: "",
  address: "",
  program: "",
  modality: "",
  message: "",
  consent: false,
});

const touched = reactive({
  fullName: false,
  docType: false,
  docNumber: false,
  phone: false,
  email: false,
  program: false,
  modality: false,
  consent: false,
});

const loading = ref(false);
const status = ref<"idle" | "success" | "error">("idle");

/** Validación */
const validFullName = computed(() => form.fullName.length >= 6 && form.fullName.includes(" "));
const validDocType = computed(() => !!form.docType);
const validDocNumber = computed(() => form.docNumber.trim().length >= 6);
const validPhone = computed(() => form.phone.replace(/\D/g, "").length >= 9);
const validEmail = computed(() => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email));
const validProgram = computed(() => !!form.program);
const validModality = computed(() => !!form.modality);
const validConsent = computed(() => form.consent);

const isValid = computed(() =>
  validFullName.value &&
  validDocType.value &&
  validDocNumber.value &&
  validPhone.value &&
  validEmail.value &&
  validProgram.value &&
  validModality.value &&
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
     * await $fetch("/api/preinscripcion", { method: "POST", body: form })
     */
    await new Promise((r) => setTimeout(r, 700));

    status.value = "success";

    // Reset
    form.fullName = "";
    form.docType = "";
    form.docNumber = "";
    form.birthDate = "";
    form.phone = "";
    form.email = "";
    form.address = "";
    form.program = "";
    form.modality = "";
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
/* ===== Preinscripción - Moderno institucional ===== */
.pre-area {
  --brand: #b1040e;
  --brand2: #8f0a12;
  --text: #0f172a;
  --muted: #64748b;
  --line: rgba(15, 23, 42, 0.10);
  --soft: rgba(177, 4, 14, 0.10);
}

/* Card form */
.pre-card {
  border-radius: 26px;
  border: 1px solid var(--line);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: 0 18px 70px rgba(2, 6, 23, 0.10);
  overflow: hidden;
}

.pre-head {
  padding: 18px 18px 8px;
  background: linear-gradient(135deg, rgba(177, 4, 14, 0.10), rgba(2, 6, 23, 0.02));
  border-bottom: 1px solid rgba(15, 23, 42, 0.10);
}

.pre-kicker {
  display: inline-flex;
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  font-weight: 900;
  color: var(--brand);
}

.pre-title {
  margin: 8px 0 6px;
  font-size: 34px;
  font-weight: 1000;
  letter-spacing: -0.04em;
  color: var(--text);
  line-height: 1.1;
}

.pre-subtitle {
  margin: 0 0 10px;
  color: var(--muted);
  font-size: 14px;
  max-width: 70ch;
}

.pre-form {
  padding: 16px 18px 18px;
}

.pre-section {
  padding: 14px 0;
  border-bottom: 1px solid rgba(15, 23, 42, 0.08);
}

.pre-section:last-child {
  border-bottom: none;
}

.pre-section-title {
  margin: 0 0 12px;
  font-size: 14px;
  font-weight: 1000;
  color: var(--text);
}

/* Grid */
.grid {
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
  background: rgba(255, 255, 255, 0.98);
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

.req {
  color: var(--brand);
  font-weight: 950;
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
.pre-actions {
  margin-top: 12px;
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

.pre-hint {
  display: grid;
  grid-template-columns: 12px 1fr;
  gap: 10px;
  align-items: start;
  padding: 10px 12px;
  border-radius: 16px;
  border: 1px solid rgba(177, 4, 14, 0.18);
  background: rgba(177, 4, 14, 0.08);
}

.pre-hint p {
  margin: 0;
  font-size: 12px;
  font-weight: 850;
  color: rgba(15, 23, 42, 0.75);
}

.hint-dot {
  width: 10px;
  height: 10px;
  background: var(--brand);
  border-radius: 50%;
  margin-top: 3px;
}

/* Alerts */
.alert {
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

/* Visual side */
.pre-visual {
  position: relative;
  min-height: 640px;
  border-radius: 28px;
  overflow: hidden;
  border: 1px solid rgba(15, 23, 42, 0.10);
  box-shadow: 0 18px 70px rgba(2, 6, 23, 0.10);
  background: radial-gradient(900px 520px at 20% 0%, rgba(177, 4, 14, 0.16), transparent 55%),
              radial-gradient(900px 520px at 120% 20%, rgba(15, 23, 42, 0.10), transparent 60%),
              rgba(255, 255, 255, 0.86);
  display: grid;
  place-items: end center;
  padding: 18px;
}

.pre-visual-bg {
  position: absolute;
  inset: 0;
  background: linear-gradient(180deg, rgba(255,255,255,0.18), rgba(255,255,255,0.0));
  pointer-events: none;
}

.pre-image {
  position: relative;
  z-index: 1;
  width: min(520px, 100%);
  height: auto;
  transform: translateY(10px);
  filter: drop-shadow(0 24px 55px rgba(2, 6, 23, 0.22));
}

/* Floating tags */
.pre-float {
  position: absolute;
  z-index: 2;
  padding: 10px 12px;
  border-radius: 18px;
  border: 1px solid rgba(15, 23, 42, 0.10);
  background: rgba(255, 255, 255, 0.92);
  box-shadow: 0 16px 45px rgba(2, 6, 23, 0.10);
}

.pre-float-1 { top: 18px; left: 18px; }
.pre-float-2 { bottom: 18px; left: 18px; }

.float-title {
  margin: 0;
  font-size: 12px;
  font-weight: 1000;
  color: var(--text);
}

.float-sub {
  margin: 3px 0 0;
  font-size: 12px;
  font-weight: 850;
  color: rgba(100, 116, 139, 0.95);
}

/* Responsive */
@media (max-width: 991px) {
  .pre-title { font-size: 28px; }
  .grid { grid-template-columns: 1fr; }
  .pre-visual { margin-top: 16px; min-height: 520px; }
  .pre-image { width: min(440px, 100%); }
}
</style>
