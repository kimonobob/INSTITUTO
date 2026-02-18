<template>
  <section class="tp-campus-choose-area apm-hero">
    <div class="container">
      <div class="row">
        <div class="col-lg-12">
          <div class="apm text-center">

            <!-- Chip -->
            <div class="apm__chip">
              <span class="apm__dot"></span>
              Proceso de Admisión
            </div>

            <!-- Título principal -->
            <h2 class="apm__title">
              Admisión transparente, por mérito
            </h2>

            <!-- Texto -->
            <p class="apm__lead">
              El Instituto de Educación Superior Tecnológico Público desarrolla su proceso de admisión conforme a la normativa vigente del Ministerio de Educación,
              garantizando transparencia y equidad. La selección se realiza considerando el cumplimiento de requisitos y el mérito académico del postulante.
            </p>

            <!-- CTA -->
            <div class="apm__actions">
              <nuxt-link href="#down" class="apm__btn">
                Ver etapas
              </nuxt-link>
            </div>

            <!-- Brillo decorativo -->
            <div class="apm__glow" aria-hidden="true"></div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts"></script>

<style scoped>
/* ===== HERO ADMISION (moderno) ===== */
.apm-hero{
  padding: 110px 0 70px;
  background: #ffffff; /* fondo blanco */
  position: relative;
  overflow: hidden;
}

/* Degradados suaves de fondo */
.apm-hero::before{
  content:"";
  position:absolute;
  inset: -120px -120px auto -120px;
  height: 420px;
  background:
    radial-gradient(500px 240px at 20% 20%, rgba(255,30,30,.16), transparent 60%),
    radial-gradient(520px 260px at 85% 30%, rgba(196,18,48,.12), transparent 62%);
  pointer-events:none;
}
.apm-hero::after{
  content:"";
  position:absolute;
  inset: auto -120px -160px -120px;
  height: 420px;
  background:
    radial-gradient(520px 260px at 30% 40%, rgba(0,0,0,.06), transparent 60%),
    radial-gradient(520px 260px at 85% 60%, rgba(255,30,30,.10), transparent 62%);
  pointer-events:none;
}

.apm{
  position: relative;
  max-width: 980px;
  margin: 0 auto;
  padding: 34px 26px 28px;
  border-radius: 28px;
  background: linear-gradient(180deg, rgba(255,255,255,.92), rgba(255,255,255,.80));
  border: 1px solid rgba(0,0,0,.06);
  box-shadow: 0 30px 80px rgba(0,0,0,.08);
  backdrop-filter: blur(8px);
}

/* Chip */
.apm__chip{
  display:inline-flex;
  align-items:center;
  gap: 10px;
  padding: 10px 14px;
  border-radius: 999px;
  color:#c41230;
  background: linear-gradient(135deg, rgba(255,30,30,.14), rgba(196,18,48,.10));
  font-weight: 950;
  letter-spacing: .8px;
  font-size: 12px;
  box-shadow: 0 18px 45px rgba(196,18,48,.12);
}
.apm__dot{
  width: 10px;
  height: 10px;
  border-radius: 999px;
  background: linear-gradient(135deg, #ff1e1e, #c41230);
  box-shadow: 0 10px 26px rgba(196,18,48,.25);
}

/* Título */
.apm__title{
  margin: 18px 0 10px;
  font-size: 52px;
  line-height: 1.06;
  letter-spacing: -1px;
  font-weight: 950;
  color:#101114;
}

/* Texto */
.apm__lead{
  margin: 0 auto 18px;
  max-width: 860px;
  font-size: 18px;
  line-height: 1.85;
  color: rgba(16,17,20,.78);
}

/* Botón */
.apm__actions{
  display:flex;
  justify-content:center;
}
.apm__btn{
  display:inline-flex;
  align-items:center;
  gap: 10px;
  height: 52px;
  padding: 0 18px;
  border-radius: 16px;
  text-decoration:none;
  color:#fff;
  font-weight: 950;
  background: linear-gradient(135deg, #ff1e1e, #c41230);
  box-shadow: 0 20px 55px rgba(196,18,48,.22);
  transition: transform .18s ease, filter .18s ease;
}
.apm__btn:hover{
  transform: translateY(-2px) scale(1.02);
  filter: brightness(0.98);
}
.apm__btn-icon{
  display:inline-flex;
  transform: translateY(1px);
}

/* Brillo */
.apm__glow{
  position:absolute;
  right: -120px;
  top: -120px;
  width: 260px;
  height: 260px;
  background: radial-gradient(circle, rgba(255,30,30,.22), transparent 65%);
  filter: blur(2px);
  pointer-events:none;
}

/* Responsive */
@media (max-width: 991px){
  .apm-hero{ padding: 90px 0 55px; }
  .apm__title{ font-size: 38px; }
  .apm__lead{ font-size: 16px; }
}
</style>
