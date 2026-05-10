<template>
  <div>
    <!-- HERO -->
    <section class="hero gradient-hero">
      <div class="container hero__inner">
        <div class="hero__content">
          <div class="badge badge-blue animate-fade-in-up">
            <svg width="12" height="12" viewBox="0 0 12 12" fill="currentColor"><circle cx="6" cy="6" r="6"/></svg>
            Trusted by 5,000+ patients
          </div>

          <h1 class="hero__title animate-fade-in-up delay-100">
            Healthy Smile<br>
            <span class="text-gradient font-serif">Starts Here</span>
          </h1>

          <p class="hero__subtitle animate-fade-in-up delay-200">
            Experience premium dental care with state-of-the-art technology, compassionate doctors, and treatments tailored to your smile.
          </p>

          <div class="hero__actions animate-fade-in-up delay-300">
            <NuxtLink to="/appointment" class="btn btn-primary btn-lg">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
              Book Appointment
            </NuxtLink>
            <NuxtLink to="/services" class="btn btn-outline btn-lg">
              View Services
            </NuxtLink>
          </div>

          <div class="hero__stats animate-fade-in-up delay-400">
            <div class="stat">
              <span class="stat__value">15+</span>
              <span class="stat__label">Years Experience</span>
            </div>
            <div class="stat-divider"></div>
            <div class="stat">
              <span class="stat__value">5K+</span>
              <span class="stat__label">Happy Patients</span>
            </div>
            <div class="stat-divider"></div>
            <div class="stat">
              <span class="stat__value">12</span>
              <span class="stat__label">Expert Doctors</span>
            </div>
            <div class="stat-divider"></div>
            <div class="stat">
              <span class="stat__value">99%</span>
              <span class="stat__label">Satisfaction Rate</span>
            </div>
          </div>
        </div>

        <div class="hero__visual animate-fade-in-up delay-200">
          <div class="hero__card-wrapper animate-float">
            <div class="hero__image-bg">
              <div class="tooth-illustration">
                <img src="/images/tooth.png" alt="Dental Clinic" />
              </div>
            </div>

            <div class="float-card float-card--top-right">
              <div class="float-card__icon">✨</div>
              <div>
                <div class="float-card__title">Premium Care</div>
                <div class="float-card__sub">ISO Certified Clinic</div>
              </div>
            </div>

            <div class="float-card float-card--bottom-left">
              <div class="float-card__icon">⭐</div>
              <div>
                <div class="float-card__title">4.9 Rating</div>
                <div class="float-card__sub">Based on 1,240 reviews</div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="hero__wave">
        <svg viewBox="0 0 1440 80" fill="none" preserveAspectRatio="none">
          <path d="M0 80L1440 80L1440 20C1200 80 960 0 720 40C480 80 240 0 0 20L0 80Z" fill="white"/>
        </svg>
      </div>
    </section>

    <!-- INTRO BANNER -->
    <section class="intro section-sm">
      <div class="container">
        <div class="intro__grid">
          <div v-for="item in introItems" :key="item.title" class="intro__item">
            <div class="intro__icon">{{ item.icon }}</div>
            <div>
              <h3>{{ item.title }}</h3>
              <p>{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- WHY CHOOSE US -->
    <section class="section why-us">
      <div class="container">
        <div class="section-header">
          <div class="badge badge-blue">Why Choose Us</div>
          <h2>Excellence in Every<br>Aspect of Dental Care</h2>
          <div class="divider"></div>
          <p>We combine cutting-edge technology with decades of expertise to deliver exceptional dental care.</p>
        </div>

        <div class="why-us__grid">
          <div v-for="(item, i) in whyItems" :key="item.title" class="why-card" :style="`animation-delay: ${i * 0.1}s`">
            <div class="why-card__icon-wrap">
              <span class="why-card__icon">{{ item.icon }}</span>
            </div>
            <h3>{{ item.title }}</h3>
            <p>{{ item.desc }}</p>
          </div>
        </div>

        <div class="why-us__cta">
          <div class="why-us__cta-inner gradient-blue">
            <div>
              <h3>Ready to Transform Your Smile?</h3>
              <p>Schedule your first consultation — completely free of charge.</p>
            </div>
            <NuxtLink to="/appointment" class="btn btn-white btn-lg">Book Free Consultation</NuxtLink>
          </div>
        </div>
      </div>
    </section>

    <!-- SERVICES PREVIEW -->
    <section class="section services-preview" style="background: var(--gray-50)">
      <div class="container">
        <div class="section-header">
          <div class="badge badge-teal">Our Services</div>
          <h2>Comprehensive Dental<br>Care Solutions</h2>
          <div class="divider"></div>
          <p>From routine check-ups to advanced implantology — we cover all your dental needs.</p>
        </div>

        <div class="grid-3">
          <div v-for="svc in previewServices" :key="svc.title" class="card service-card">
            <div class="service-card__icon">{{ svc.icon }}</div>
            <h3>{{ svc.title }}</h3>
            <p>{{ svc.desc }}</p>
            <div class="service-card__footer">
              <span class="service-card__price">From {{ svc.price }}</span>
              <NuxtLink to="/appointment" class="btn btn-primary">Book Now</NuxtLink>
            </div>
          </div>
        </div>

        <div class="section-cta">
          <NuxtLink to="/services" class="btn btn-outline btn-lg">View All Services</NuxtLink>
        </div>
      </div>
    </section>

    <!-- TESTIMONIALS -->
    <section class="section testimonials">
      <div class="container">
        <div class="section-header">
          <div class="badge badge-blue">Patient Stories</div>
          <h2>What Our Patients Say</h2>
          <div class="divider"></div>
          <p>Real experiences from real patients who chose DentaCare Premium.</p>
        </div>

        <div class="grid-3">
          <div v-for="t in testimonials" :key="t.name" class="testimonial-card card">
            <div class="stars">
              <span v-for="s in 5" :key="s">⭐</span>
            </div>
            <p class="testimonial-text">"{{ t.text }}"</p>
            <div class="testimonial-author">
              <div class="testimonial-avatar">{{ t.name[0] }}</div>
              <div>
                <div class="testimonial-name">{{ t.name }}</div>
                <div class="testimonial-service">{{ t.service }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- EMERGENCY BANNER -->
    <section class="emergency-banner gradient-teal-blue">
      <div class="container emergency-banner__inner">
        <div class="emergency-banner__left">
          <div class="emergency-banner__pulse">
            <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
          </div>
          <div>
            <h3>Dental Emergency?</h3>
            <p>We're available for urgent cases 24/7. Don't wait — call us immediately.</p>
          </div>
        </div>
        <div class="emergency-banner__actions">
          <a href="tel:+48999111222" class="btn btn-white btn-lg">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81a19.79 19.79 0 01-3.07-8.63A2 2 0 012 0h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/></svg>
            Emergency: +48 999 111 222
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const introItems = [
  { icon: '🏥', title: 'Modern Clinic', desc: 'State-of-the-art equipment and sterile environment' },
  { icon: '👨‍⚕️', title: 'Expert Team', desc: '12 board-certified dental specialists' },
  { icon: '💙', title: 'Patient First', desc: 'Personalized care and pain-free procedures' },
  { icon: '🌟', title: 'Premium Quality', desc: 'ISO certified with guaranteed results' },
]

const whyItems = [
  { icon: '🔬', title: 'Advanced Technology', desc: 'Digital X-rays, 3D scans, laser dentistry, and CAD/CAM restorations for precision treatment.' },
  { icon: '😴', title: 'Painless Treatments', desc: 'Sedation options and gentle techniques ensure you feel relaxed and comfortable throughout.' },
  { icon: '🛡️', title: 'Safety First', desc: 'Strict sterilization protocols and use of certified, biocompatible materials for every procedure.' },
  { icon: '⚡', title: 'Fast Results', desc: 'Same-day crowns, express whitening, and urgent appointments available when you need them most.' },
  { icon: '💳', title: 'Flexible Payment', desc: 'Interest-free installment plans and major insurance accepted to make quality care accessible.' },
  { icon: '🌍', title: 'Multilingual Staff', desc: 'Our team speaks English, Polish, Ukrainian, and German — so you always feel at home.' },
]

const previewServices = [
  { icon: '🦷', title: 'Teeth Cleaning', desc: 'Professional ultrasonic scaling and polishing to remove tartar and restore natural shine.', price: '€50' },
  { icon: '✨', title: 'Teeth Whitening', desc: 'Professional in-office whitening that lifts stains up to 8 shades in a single session.', price: '€200' },
  { icon: '🔩', title: 'Dental Implants', desc: 'Permanent titanium implants that look, feel and function like your natural teeth.', price: '€1,200' },
]

const testimonials = [
  { name: 'Maria S.', service: 'Teeth Whitening', text: 'I was nervous about whitening but the team made me feel so comfortable. My smile is completely transformed!' },
  { name: 'James K.', service: 'Dental Implants', text: 'Had two implants done here. The procedure was painless and the results are incredible. Highly recommend!' },
  { name: 'Anna P.', service: 'Orthodontics', text: 'My daughter had braces here for 18 months. Dr. Kowalska is amazing — so patient and professional. Beautiful result.' },
]
</script>

<style scoped>
/* HERO */
.hero {
  padding-top: 7rem;
  padding-bottom: 0;
  position: relative;
  overflow: hidden;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.hero__inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
  flex: 1;
  padding-top: 2rem;
  padding-bottom: 6rem;
}

.hero__content {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.hero__title {
  font-family: var(--font-serif);
  font-size: clamp(2.5rem, 5vw, 3.75rem);
  color: var(--gray-900);
  line-height: 1.1;
}

.hero__subtitle {
  font-size: 1.15rem;
  color: var(--gray-500);
  line-height: 1.7;
  max-width: 460px;
}

.hero__actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.hero__stats {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  padding-top: 0.5rem;
  flex-wrap: wrap;
}

.stat { text-align: center; }

.stat__value {
  display: block;
  font-size: 1.75rem;
  font-weight: 800;
  color: var(--blue-700);
  line-height: 1;
}

.stat__label {
  font-size: 0.75rem;
  color: var(--gray-500);
  font-weight: 500;
  white-space: nowrap;
}

.stat-divider {
  width: 1px;
  height: 40px;
  background: var(--gray-200);
}

.hero__visual {
  display: flex;
  justify-content: center;
  align-items: center;
}

.hero__card-wrapper {
  position: relative;
  width: 340px;
  height: 380px;
}

.hero__image-bg {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, white, var(--blue-50));
  border-radius: 2rem;
  box-shadow: var(--shadow-2xl);
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--blue-100);
}

.tooth-illustration {
  opacity: 0.85;
}

.float-card {
  position: absolute;
  background: white;
  border-radius: var(--radius-lg);
  padding: 0.75rem 1.1rem;
  box-shadow: var(--shadow-xl);
  display: flex;
  align-items: center;
  gap: 0.625rem;
  border: 1px solid var(--gray-100);
}

.float-card--top-right { top: -1rem; right: -1.5rem; }
.float-card--bottom-left { bottom: 1.5rem; left: -1.5rem; }

.float-card__icon { font-size: 1.5rem; }
.float-card__title { font-weight: 700; font-size: 0.875rem; color: var(--gray-900); }
.float-card__sub { font-size: 0.75rem; color: var(--gray-500); }

.hero__wave {
  width: 100%;
  line-height: 0;
}

.hero__wave svg { display: block; width: 100%; height: 60px; }

/* INTRO */
.intro__grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 2rem;
}

.intro__item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.intro__icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.intro__item h3 {
  font-size: 0.975rem;
  font-weight: 700;
  color: var(--gray-900);
  margin-bottom: 0.25rem;
}

.intro__item p {
  font-size: 0.875rem;
  color: var(--gray-500);
}

/* WHY US */
.why-us__grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.75rem;
  margin-bottom: 3rem;
}

.why-card {
  padding: 2rem;
  border-radius: var(--radius-xl);
  background: white;
  box-shadow: var(--shadow-md);
  transition: all 0.3s ease;
  border: 1px solid var(--gray-100);
}

.why-card:hover {
  box-shadow: var(--shadow-xl);
  transform: translateY(-4px);
  border-color: var(--blue-200);
}

.why-card__icon-wrap {
  width: 56px;
  height: 56px;
  background: linear-gradient(135deg, var(--blue-50), #e0f2fe);
  border-radius: var(--radius-md);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.25rem;
}

.why-card__icon { font-size: 1.75rem; }

.why-card h3 {
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--gray-900);
  margin-bottom: 0.625rem;
}

.why-card p { font-size: 0.9rem; color: var(--gray-500); line-height: 1.6; }

.why-us__cta { margin-top: 1rem; }

.why-us__cta-inner {
  border-radius: var(--radius-2xl);
  padding: 2.5rem 3rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  flex-wrap: wrap;
}

.why-us__cta-inner h3 { font-family: var(--font-serif); font-size: 1.5rem; color: white; margin-bottom: 0.375rem; }
.why-us__cta-inner p { color: rgb(255 255 255 / 0.8); font-size: 0.95rem; }

/* SERVICE CARDS */
.service-card {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.service-card__icon {
  font-size: 2.5rem;
  margin-bottom: 0.25rem;
}

.service-card h3 { font-size: 1.1rem; font-weight: 700; color: var(--gray-900); }
.service-card p { font-size: 0.9rem; color: var(--gray-500); line-height: 1.6; flex: 1; }

.service-card__footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: auto;
  padding-top: 1rem;
  border-top: 1px solid var(--gray-100);
}

.service-card__price {
  font-weight: 800;
  font-size: 1.2rem;
  color: var(--blue-700);
}

.section-cta {
  text-align: center;
  margin-top: 3rem;
}

/* TESTIMONIALS */
.testimonial-card {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.stars { font-size: 0.9rem; letter-spacing: 2px; }

.testimonial-text {
  font-size: 0.95rem;
  color: var(--gray-600);
  line-height: 1.7;
  font-style: italic;
  flex: 1;
}

.testimonial-author {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.testimonial-avatar {
  width: 44px;
  height: 44px;
  border-radius: var(--radius-full);
  background: linear-gradient(135deg, var(--blue-500), var(--teal-500));
  color: white;
  font-weight: 700;
  font-size: 1.1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.testimonial-name { font-weight: 700; font-size: 0.9rem; color: var(--gray-900); }
.testimonial-service { font-size: 0.8rem; color: var(--blue-500); font-weight: 500; }

/* EMERGENCY */
.emergency-banner { padding: 2.25rem 0; }

.emergency-banner__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  flex-wrap: wrap;
}

.emergency-banner__left {
  display: flex;
  align-items: center;
  gap: 1.25rem;
}

.emergency-banner__pulse {
  width: 56px;
  height: 56px;
  border-radius: var(--radius-full);
  background: rgba(255,255,255,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  animation: pulse-ring 2s ease infinite;
  flex-shrink: 0;
}

.emergency-banner__left h3 { color: white; font-size: 1.25rem; margin-bottom: 0.25rem; }
.emergency-banner__left p { color: rgba(255,255,255,0.85); font-size: 0.9rem; }

@media (max-width: 1024px) {
  .hero__inner { grid-template-columns: 1fr; text-align: center; }
  .hero__subtitle { margin: 0 auto; }
  .hero__actions { justify-content: center; }
  .hero__stats { justify-content: center; }
  .hero__visual { display: none; }
  .intro__grid { grid-template-columns: repeat(2, 1fr); }
  .why-us__grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 640px) {
  .intro__grid { grid-template-columns: 1fr; }
  .why-us__grid { grid-template-columns: 1fr; }
  .why-us__cta-inner { flex-direction: column; text-align: center; }
  .emergency-banner__inner { flex-direction: column; text-align: center; }
  .emergency-banner__left { flex-direction: column; text-align: center; }
}
</style>
