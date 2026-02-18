<template>
    <section class="tp-tution-area grey-bg pt-120 pb-120">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div v-for="item in deadlines_data" :key="item.id" class="tp-dates-box mb-20">
                        <div class="tp-tution-table tp-dates-table">
                            <h3 class="tp-dates-title">
                                <span v-html="item.icon"></span>
                                {{ item.title }}
                            </h3>
                            <ul>
                                <li class="tp-tution-table-head">
                                    <div class="tp-course-table-row">
                                        <div class="tp-dates-month">
                                            <h4 class="tp-tution-table-title">{{ item.date }}</h4>
                                        </div>
                                        <div class="tp-dates-date">
                                            <h4 class="tp-tution-table-title">Date</h4>
                                        </div>
                                    </div>
                                </li>
                                <li v-for="sd in item.scheduleData" :key="sd.id"
                                    :class="['tp-tution-table-inner', { none: sd.isLast }]">
                                    <div class="tp-course-table-row">
                                        <div class="tp-dates-month">
                                            <h4 class="tp-tution-inner">{{ sd.title }}</h4>
                                        </div>
                                        <div class="tp-dates-date">
                                            <h4 class="tp-tution-inner">{{ sd.date }}</h4>
                                        </div>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">

const deadlines_data = [
    {
        id: 1,
        icon: `<svg width="22" height="23" viewBox="0 0 22 23" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="11" cy="11" r="10" stroke="#B1040E" stroke-width="2"/>
                <path d="M11 6V11L14 13" stroke="#B1040E" stroke-width="2" stroke-linecap="round"/>
               </svg>`,
        title: "Convocatoria y Registro",
        date: "Enero – Febrero 2026",
        scheduleData: [
            {
                id: 1,
                title: "Publicación de Convocatoria",
                date: "06 de enero 2026",
            },
            {
                id: 2,
                title: "Inscripciones en línea y presencial",
                date: "08 enero – 20 febrero 2026",
            },
            {
                id: 3,
                title: "Entrega de expediente",
                date: "Hasta el 21 febrero 2026",
            },
            {
                id: 4,
                title: "Cierre de Inscripciones",
                date: "21 febrero 2026",
                isLast: true,
            },
        ],
    },
    {
        id: 2,
        icon: `<svg width="22" height="23" viewBox="0 0 22 23" fill="none">
                <rect x="3" y="5" width="16" height="14" rx="2" stroke="#B1040E" stroke-width="2"/>
                <path d="M3 9H19" stroke="#B1040E" stroke-width="2"/>
               </svg>`,
        title: "Evaluación y Resultados",
        date: "Marzo 2026",
        scheduleData: [
            {
                id: 1,
                title: "Examen de Admisión",
                date: "01 marzo 2026",
            },
            {
                id: 2,
                title: "Publicación de Resultados",
                date: "03 marzo 2026",
            },
            {
                id: 3,
                title: "Periodo de Reclamos",
                date: "04 – 05 marzo 2026",
            },
            {
                id: 4,
                title: "Lista Oficial de Ingresantes",
                date: "06 marzo 2026",
                isLast: true,
            },
        ],
    },
    {
        id: 3,
        icon: `<svg width="22" height="23" viewBox="0 0 22 23" fill="none">
                <path d="M4 6H18V17H4V6Z" stroke="#B1040E" stroke-width="2"/>
                <path d="M4 9H18" stroke="#B1040E" stroke-width="2"/>
               </svg>`,
        title: "Matrícula",
        date: "Marzo 2026",
        scheduleData: [
            {
                id: 1,
                title: "Matrícula Ordinaria",
                date: "10 – 15 marzo 2026",
            },
            {
                id: 2,
                title: "Matrícula Extemporánea",
                date: "18 – 20 marzo 2026",
            },
            {
                id: 3,
                title: "Inicio de Clases",
                date: "24 marzo 2026",
                isLast: true,
            },
        ],
    },
    {
        id: 4,
        icon: `<svg width="22" height="23" viewBox="0 0 22 23" fill="none">
                <circle cx="11" cy="11" r="8" stroke="#B1040E" stroke-width="2"/>
                <path d="M8 11L10 13L14 9" stroke="#B1040E" stroke-width="2" stroke-linecap="round"/>
               </svg>`,
        title: "Modalidades Especiales",
        date: "Proceso Complementario 2026",
        scheduleData: [
            {
                id: 1,
                title: "Traslados Internos y Externos",
                date: "Abril 2026",
            },
            {
                id: 2,
                title: "Reingresos",
                date: "Abril 2026",
            },
            {
                id: 3,
                title: "Admisión Extraordinaria",
                date: "Según cronograma oficial",
                isLast: true,
            },
        ],
    },
];

</script>