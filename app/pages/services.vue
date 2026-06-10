<template>
  <div>
    <!-- Page Hero -->
    <section class="page-hero gradient-hero">
      <div class="container page-hero__inner">
        <div class="badge badge-blue">Our Services</div>
        <h1 class="font-serif">Complete Dental Care<br><span class="text-gradient">Under One Roof</span></h1>
        <p>From preventive check-ups to complex implantology — our expert team delivers exceptional results at every visit.</p>
      </div>
      <div class="page-hero__wave">
        <svg viewBox="0 0 1440 60" fill="none" preserveAspectRatio="none">
          <path d="M0 60L1440 60L1440 15C1200 60 960 0 720 30C480 60 240 0 0 15L0 60Z" fill="white"/>
        </svg>
      </div>
    </section>

    <!-- Services Grid -->
    <section class="section">
      <div class="container">
        <div class="services-grid">
          <div
            v-for="(svc, i) in services"
            :key="svc.title"
            class="service-card card"
            :style="`animation-delay:${i * 0.08}s`"
          >
            <div v-if="svc.videoUrl" class="service-card__video" @click="openVideo(svc.videoUrl)">
              <video
                :src="svc.videoUrl"
                autoplay
                muted
                loop
                playsinline
              />
            </div>

            <div class="service-card__header">
              <div class="service-card__icon-wrap">
                <span>{{ svc.icon }}</span>
              </div>
              <div class="service-card__badge" :style="`background:${svc.badgeBg};color:${svc.badgeColor}`">
                {{ svc.category }}
              </div>
            </div>

            <h3>{{ svc.title }}</h3>
            <p class="service-card__desc">{{ svc.desc }}</p>

            <ul class="service-card__features">
              <li v-for="f in svc.features" :key="f">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg>
                {{ f }}
              </li>
            </ul>

            <div class="service-card__footer">
              <div class="service-card__price-wrap">
                <span class="service-card__price-label">Starting from</span>
                <span class="service-card__price">{{ svc.price }}</span>
              </div>
              <div class="service-card__actions">
                <NuxtLink to="/appointment" class="btn btn-primary" @click.stop>Book Now</NuxtLink>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Info Strip -->
    <section class="info-strip gradient-blue">
      <div class="container info-strip__inner">
        <div v-for="item in infoItems" :key="item.title" class="info-item">
          <div class="info-item__icon">{{ item.icon }}</div>
          <div class="info-item__title">{{ item.title }}</div>
          <div class="info-item__desc">{{ item.desc }}</div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({ title: 'Services — DentaCare Premium' })

function openVideo(url) {
  window.open(url, '_blank')
}

const services = [
  {
    icon: '🦷', title: 'Teeth Cleaning', category: 'Prevention', price: '€50',
    badgeBg: '#eff6ff', badgeColor: '#2563eb',
    desc: 'Professional ultrasonic scaling and polishing that removes hardened tartar, surface stains, and bacteria to restore your natural shine.',
    videoUrl: '/videos/teeth-cleaning.mp4',
    features: ['Ultrasonic scaling', 'Polishing & stain removal', 'Fluoride treatment', 'Oral hygiene advice'],
  },
  {
    icon: '🔍', title: 'Caries Treatment', category: 'Prevention', price: '€120',
    badgeBg: '#eff6ff', badgeColor: '#2563eb',
    desc: 'Early detection and treatment of tooth decay using tooth-colored composite fillings that blend seamlessly with your natural teeth.',
    videoUrl: '/videos/carries-treatment.mp4',
    features: ['Digital X-ray diagnosis', 'Composite (white) filling', 'Minimally invasive', 'Same-day treatment'],
  },
  {
    icon: '✨', title: 'Teeth Whitening', category: 'Cosmetic', price: '€200',
    badgeBg: '#fdf4ff', badgeColor: '#9333ea',
    desc: 'Professional in-office whitening using certified bleaching agents that lift stains up to 8 shades in a single 90-minute session.',
    videoUrl: '/videos/teeth-whitening.mp4',
    features: ['Up to 8 shades lighter', 'Safe LED activation', '90-minute session', 'Take-home maintenance kit'],
  },
  {
    icon: '🔩', title: 'Dental Implants', category: 'Surgery', price: '€1,200',
    badgeBg: '#fff7ed', badgeColor: '#ea580c',
    desc: 'Permanent titanium root implants topped with custom ceramic crowns that look, feel, and function exactly like your natural teeth.',
    features: ['Titanium Swiss implant', 'Custom ceramic crown', '3D CT planning', '10-year guarantee'],
  },
  {
    icon: '📐', title: 'Orthodontics', category: 'Orthodontics', price: 'from €900',
    badgeBg: '#f0fdf4', badgeColor: '#16a34a',
    desc: 'Metal brackets, ceramic braces, or clear aligners — we tailor your treatment plan to achieve the perfect smile alignment.',
    features: ['Metal, ceramic, or clear aligners', 'Digital treatment preview', 'Regular adjustments included', 'Retainers after treatment'],
  },
  {
    icon: '💉', title: 'Root Canal Treatment', category: 'Surgery', price: '€250',
    badgeBg: '#fff7ed', badgeColor: '#ea580c',
    desc: 'Gentle endodontic treatment that saves infected teeth by removing the damaged pulp and sealing the canal against reinfection.',
    features: ['Painless under anesthesia', 'Rotary file technology', 'Single or multi-visit', 'Crown restoration option'],
  },
]


const infoItems = [
  { icon: '📋', title: 'Free Consultation', desc: 'Your first exam and treatment plan is always free.' },
  { icon: '💳', title: 'Flexible Payment', desc: 'Split any treatment into 12 interest-free installments.' },
  { icon: '🛡️', title: 'Treatment Guarantee', desc: '2-year warranty on all fillings and crowns.' },
  { icon: '⚡', title: 'Same-Day Bookings', desc: 'Urgent appointments available within 24 hours.' },
]
</script>

<style scoped>
.page-hero {
  padding: 9rem 0 0;
  text-align: center;
  position: relative;
}

.page-hero__inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.25rem;
  padding-bottom: 4rem;
}

.page-hero__inner h1 {
  font-size: clamp(2rem, 4vw, 3rem);
}

.page-hero__inner p {
  max-width: 540px;
  color: var(--gray-500);
  font-size: 1.1rem;
}

.page-hero__wave { line-height: 0; }
.page-hero__wave svg { display: block; width: 100%; height: 50px; }

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.75rem;
}

.service-card {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0.875rem;
  overflow: hidden;
}

.service-card__video {
  margin: -2rem -2rem 0;
  height: 160px;
  border-radius: var(--radius-lg) var(--radius-lg) 0 0;
  overflow: hidden;
  background: var(--gray-100);
  cursor: pointer;
}

.service-card__video video {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.service-card__header {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
}

.service-card__icon-wrap {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, var(--blue-50), #e0f2fe);
  border-radius: var(--radius-md);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
}

.service-card__badge {
  padding: 0.3rem 0.75rem;
  border-radius: var(--radius-full);
  font-size: 0.75rem;
  font-weight: 600;
}

.service-card h3 {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--gray-900);
}

.service-card__desc {
  font-size: 0.9rem;
  color: var(--gray-500);
  line-height: 1.65;
}

.service-card__features {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  flex: 1;
}

.service-card__features li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.875rem;
  color: var(--gray-600);
}

.service-card__features svg { color: var(--teal-500); flex-shrink: 0; }

.service-card__footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 1rem;
  border-top: 1px solid var(--gray-100);
  margin-top: auto;
}

.service-card__actions {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}


.service-card__price-label {
  display: block;
  font-size: 0.75rem;
  color: var(--gray-400);
  font-weight: 500;
}

.service-card__price {
  font-size: 1.35rem;
  font-weight: 800;
  color: var(--blue-700);
}

.info-strip { padding: 3rem 0; }

.info-strip__inner {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2rem;
  text-align: center;
}

.info-item__icon { font-size: 2.25rem; margin-bottom: 0.625rem; }
.info-item__title { font-weight: 700; color: white; margin-bottom: 0.375rem; }
.info-item__desc { font-size: 0.875rem; color: rgba(255,255,255,0.75); }

@media (max-width: 1024px) {
  .services-grid { grid-template-columns: repeat(2, 1fr); }
  .info-strip__inner { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 640px) {
  .services-grid { grid-template-columns: 1fr; }
  .info-strip__inner { grid-template-columns: 1fr; }
}
</style>
