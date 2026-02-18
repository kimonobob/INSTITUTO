<template>
  <div class="megamenu-pop">
    <div class="megamenu-box">
      <div class="megamenu-grid">
        <div
          v-for="pd in pagesDropdown"
          :key="pd.id"
          class="megamenu-col"
          :class="{ 'is-two': pd.id === 2 }"
        >
          <!-- Normal -->
          <div v-if="pd.id !== 2" class="megamenu-list">
            <h4 class="megamenu-title">{{ pd.title }}</h4>
            <ul class="megamenu-ul">
              <li v-for="sm in pd.dropdown_menus" :key="sm.id" class="megamenu-li">
                <NuxtLink :to="sm.link" class="megamenu-link">
                  {{ sm.title }}
                </NuxtLink>
              </li>
            </ul>
          </div>

          <!-- Caso especial: 2 columnas -->
          <div v-else class="megamenu-list">
            <h4 class="megamenu-title">{{ pd.title }}</h4>

            <div class="megamenu-two-cols">
              <ul class="megamenu-ul">
                <li v-for="sm in pd.dropdown_menus.slice(0, 6)" :key="sm.id" class="megamenu-li">
                  <NuxtLink :to="sm.link" class="megamenu-link">
                    {{ sm.title }}
                  </NuxtLink>
                </li>
              </ul>

              <ul class="megamenu-ul">
                <li v-for="sm in pd.dropdown_menus.slice(6)" :key="sm.id" class="megamenu-li">
                  <NuxtLink :to="sm.link" class="megamenu-link">
                    {{ sm.title }}
                  </NuxtLink>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { IPagesDropdown } from '@/types/menu-d-t';
defineProps<{ pagesDropdown: IPagesDropdown[] }>()
</script>

<style scoped>
/* CONTENEDOR del dropdown:
   - evita fullwidth
   - se ajusta al contenido
*/
.megamenu-pop {
  width: auto;
}

/* CAJA del dropdown */
.megamenu-box {
  width: fit-content;              /* clave: no se estira */
  max-width: 420px;                /* ajusta aquí si quieres más angosto/ancho */
  min-width: 260px;
  padding: 14px 16px;              /* menos padding = menos “ventana gigante” */
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 12px 30px rgba(0,0,0,.12);
}

/* Grid compacto (para 1 columna normalmente) */
.megamenu-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 14px;
}

/* Columna */
.megamenu-col {
  min-width: 0;
}

/* Cuando sea el caso 2 columnas, dejamos más ancho */
.megamenu-col.is-two .megamenu-box {
  max-width: 560px;
}

/* Título */
.megamenu-title {
  font-size: 14px;
  font-weight: 700;
  margin: 0 0 10px 0;
  color: #111;
}

/* UL limpio */
.megamenu-ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

/* Espaciado de items más compacto */
.megamenu-li {
  margin: 0 0 6px 0;
}

/* Link */
.megamenu-link {
  display: inline-block;
  font-size: 13.5px;
  line-height: 1.25;
  color: #333;
  text-decoration: none;
  padding: 3px 0;
  transition: .2s ease;
}

.megamenu-link:hover {
  color: #b00020;
}

/* 2 columnas (solo para id === 2) */
.megamenu-two-cols {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 18px;
}

/* Por si hay muchos items, que no crezca infinito */
.megamenu-box {
  max-height: 70vh;
  overflow: auto;
}
</style>
