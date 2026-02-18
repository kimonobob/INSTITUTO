
<template>
    <section class="plan-area tp-plan-4-wrap fix">
        <div class="container">
            <div class="row">
                <div class="col-lg-3">
                    <div class="tp-plan-4-section">
                        <span>Instituto de Educación Superior Tecnológico Púbico</span>
                        <h3 class="tp-plan-4-section-title">Conoce Nuestros Programas</h3>
                    </div>
                </div>
                <div class="col-lg-9">
                    <div class="tp-plan-4-wrapper">
                        <div class="row">
                            <div v-for="item in planData" :key="item.id" class="col-md-4">
                                <div class="tp-plan-4-item" :class="{ active: activeId === item.id }"
                                    @mouseenter="setActiveId(item.id)" @click="navigate(item.link)">
                                    <div class="tp-plan-4-bg" :style="{ backgroundImage: `url(${item.image})` }"></div>
                                    <div class="tp-plan-4-content d-flex align-items-center justify-content-center">
                                        <div class="tp-plan-4-box text-center">
                                            <span>{{ item.id <= 9 ? `0${item.id}` : item.id }}</span>
                                            <h4 class="tp-plan-4-title" v-html="item.title"></h4>
                                            <p>{{ item.description }}</p>
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

const router = useRouter();
const activeId = ref(1);

const planData = [
    {
        id: 1,
        title: "Enfermería Técnica",
        description: "Área Salud",
        image: "/images/bg/plan/enf.png",
        link: "/enfermeria-tecnica",
    },
    {
        id: 2,
        title: "Arquitectura de <br/> Plataformas y Servicios <br/> de Tecnologías de Información",
        description: "Área de Tecnología e Informática",
        image: "/images/bg/plan/atic.png",
        link: "/arquitectura-de-plataformas",
    },
    {
        id: 3,
        title: "Contabilidad",
        description: "Área Empresarial",
        image: "/images/bg/plan/cnt.png",
        link: "/contabilidad",
    },
    {
        id: 4,
        title: "Producción <br/> Agropecuaria",
        description: "Área Agropecuaria",
        image: "/images/bg/plan/ag.png",
        link: "/produccion-agropecuaria",
    },{
        id: 5,
        title: "Industrias <br/> Alimentarias",
        description: "Área de Industrias Alimentarias",
        image: "/images/bg/plan/ind.png",
        link: "/industrias-alimentarias",
    },
];

const setActiveId = (id: number) => {
    activeId.value = id;
};

const navigate = (link: string) => {
    router.push(link);
};
</script>
