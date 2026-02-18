<template>
  <section class="max-w-7xl mx-auto px-4 sm:px-6 grid grid-cols-1 lg:grid-cols-2 gap-12 items-start">
    <!-- IZQUIERDA -->
    <div class="w-full">
      <!-- Título -->
      <header>
        <h1 class="text-4xl sm:text-5xl font-extrabold text-[#0A2540]">
          Contabilidad
        </h1>
        <div class="w-20 h-1.5 mt-4 bg-red-500"></div>
      </header>

      <!-- Descripción -->
      <div class="mt-6 text-slate-600 text-lg space-y-4">
        <p>¿Apasionado por las finanzas y el orden empresarial?</p>
        <p>
          Te formamos como un profesional clave para la gestión contable, financiera y tributaria
          de cualquier organización, con enfoque práctico y herramientas actuales.
        </p>
        <p>
          <strong class="text-[#0A2540]">Con la Carrera de Contabilidad</strong>, podrás interpretar estados
          financieros, optimizar recursos y apoyar la toma de decisiones.
        </p>
      </div>

      <!-- Fichas -->
      <div class="mt-12 grid grid-cols-1 sm:grid-cols-2 gap-6">
        <InfoCard title="Inicio" subtitle="Consultar inicio">
          <IconCalendarCheck />
        </InfoCard>

        <InfoCard title="Turno" subtitle="Mañana / Tarde / Noche">
          <IconClock />
        </InfoCard>

        <InfoCard title="Modalidad" subtitle="Presencial">
          <IconColumns />
        </InfoCard>

        <InfoCard title="Duración" subtitle="3 años">
          <IconCalendarCheck />
        </InfoCard>
      </div>
    </div>

    <!-- DERECHA (STICKY) -->
    <aside class="w-full lg:sticky lg:top-10">
      <div class="bg-white rounded-3xl shadow-2xl w-full max-w-md mx-auto overflow-hidden">
        <div class="bg-[#002a5d] p-8 text-center">
          <p class="text-white text-lg">Déjanos tus datos y te contactaremos</p>
          <h3 class="text-white text-3xl font-bold">Solicita más información aquí</h3>
        </div>

        <form class="p-8 space-y-5" @submit.prevent="onSubmit">
          <input
            v-model="form.dni"
            name="dni"
            type="text"
            required
            placeholder="DNI"
            class="w-full p-4 bg-slate-100 rounded-2xl border border-slate-200 focus:outline-none focus:ring-2 focus:ring-[#002a5d]"
          />
          <input
            v-model="form.nombres"
            name="nombres"
            type="text"
            required
            placeholder="Nombres"
            class="w-full p-4 bg-slate-100 rounded-2xl border border-slate-200 focus:outline-none focus:ring-2 focus:ring-[#002a5d]"
          />
          <input
            v-model="form.telefono"
            name="telefono"
            type="tel"
            required
            placeholder="Teléfono"
            class="w-full p-4 bg-slate-100 rounded-2xl border border-slate-200 focus:outline-none focus:ring-2 focus:ring-[#002a5d]"
          />
          <select
            v-model="form.carrera"
            name="carrera"
            required
            class="w-full p-4 bg-slate-100 rounded-2xl border border-slate-200 focus:outline-none focus:ring-2 focus:ring-[#002a5d] appearance-none"
          >
            <option value="" disabled>Elige una carrera</option>
            <option value="Enfermería Técnica">Enfermería Técnica</option>
            <option value="Contabilidad">Contabilidad</option>
            <option value="Producción Agropecuaria">Producción Agropecuaria</option>
            <option value="Industrias Alimentarias">Industrias Alimentarias</option>
            <option value="Arquitectura de Plataformas TI">Arquitectura de Plataformas TI</option>
          </select>

          <button
            type="submit"
            class="w-full bg-red-500 text-white font-bold py-4 rounded-2xl hover:bg-red-600 transition-colors duration-300"
          >
            Enviar
          </button>
        </form>
      </div>
    </aside>
  </section>
</template>

<script setup lang="ts">
import { reactive } from "vue";

const form = reactive({
  dni: "",
  nombres: "",
  telefono: "",
  carrera: "",
});

const onSubmit = () => {
  // Aquí conectas tu API / WhatsApp / Email
  console.log("Formulario:", { ...form });
};
</script>

<!-- Componentes internos (reutilizables) -->
<script lang="ts">
import { defineComponent } from "vue";

export const InfoCard = defineComponent({
  name: "InfoCard",
  props: {
    title: { type: String, required: true },
    subtitle: { type: String, required: true },
  },
  setup(props, { slots }) {
    return () => (
      <div class="bg-white rounded-2xl p-6 text-center flex flex-col items-center shadow-lg hover:shadow-xl hover:-translate-y-1 transition-all duration-300">
        <div class="w-12 h-12 mb-4">{slots.default?.()}</div>
        <h3 class="text-lg font-bold text-[#0A2540]">{props.title}</h3>
        <p class="text-slate-500 mt-1">{props.subtitle}</p>
      </div>
    );
  },
});

export const IconCalendarCheck = defineComponent({
  name: "IconCalendarCheck",
  setup() {
    return () => (
      <svg class="w-12 h-12" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M8 2V5" stroke="#0A2540" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
        <path d="M16 2V5" stroke="#0A2540" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
        <path d="M3.5 9.08984H20.5" stroke="#0A2540" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
        <path
          d="M21 8.5V17C21 20 19.5 22 16.5 22H7.5C4.5 22 3 20 3 17V8.5C3 5.5 4.5 3.5 7.5 3.5H16.5C19.5 3.5 21 5.5 21 8.5Z"
          stroke="#0A2540"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path d="M11.9945 13.6992L10.3445 15.3492L8.5 13.5" stroke="#EF4444" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
      </svg>
    );
  },
});

export const IconClock = defineComponent({
  name: "IconClock",
  setup() {
    return () => (
      <svg class="w-12 h-12" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M22 12C22 17.52 17.52 22 12 22C6.48 22 2 17.52 2 12C2 6.48 6.48 2 12 2C17.52 2 22 6.48 22 12Z" stroke="#0A2540" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
        <path d="M12 7V12L15 13.5" stroke="#0A2540" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
      </svg>
    );
  },
});

export const IconColumns = defineComponent({
  name: "IconColumns",
  setup() {
    return () => (
      <svg class="w-12 h-12" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M2 18.27V9.73C2 5.73 3.73 4 7.73 4H16.27C20.27 4 22 5.73 22 9.73V14.27C22 18.27 20.27 20 16.27 20H7.73C3.73 20 2 18.27 2 14.27V9.73"
          stroke="#0A2540"
          stroke-width="1.5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path d="M12 4V20" stroke="#0A2540" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" />
      </svg>
    );
  },
});
</script>
