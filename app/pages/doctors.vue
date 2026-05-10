<template>
  <div>
    <section class="page-hero gradient-hero">
      <div class="container page-hero__inner">
        <div class="badge badge-blue">Our Team</div>
        <h1 class="font-serif">Meet Our Expert <span class="text-gradient">Doctors</span></h1>
        <p>A passionate team of board-certified specialists dedicated to your smile and well-being.</p>
      </div>
      <div class="page-hero__wave">
        <svg viewBox="0 0 1440 60" fill="none" preserveAspectRatio="none">
          <path d="M0 60L1440 60L1440 15C1200 60 960 0 720 30C480 60 240 0 0 15L0 60Z" fill="white"/>
        </svg>
      </div>
    </section>

    <section class="section">
      <div class="container">
        <div class="doctors-grid">
          <div v-for="(doc, i) in doctors" :key="doc.name" class="doctor-card" :style="`animation-delay:${i * 0.1}s`">
            <!-- Photo -->
            <div class="doctor-card__photo">
              <img :src="doc.img" :alt="doc.name" />
              <div class="doctor-card__overlay">
                <span class="doctor-card__specialty-pill">{{ doc.specialty }}</span>
                <div class="doctor-card__exp-badge">
                  <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
                  {{ doc.experience }} yrs exp.
                </div>
              </div>
            </div>

            <!-- Body -->
            <div class="doctor-card__body">
              <h3>{{ doc.name }}</h3>
              <p class="doctor-card__bio">{{ doc.bio }}</p>

              <div class="doctor-card__meta">
                <div class="doctor-card__meta-item">
                  <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
                  {{ doc.days }}
                </div>
                <div class="doctor-card__meta-item">
                  <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 5h12M9 3v2m1.048 9.5A18.022 18.022 0 016.412 9m6.088 9h7M11 21l5-10 5 10M12.751 5C11.783 10.77 8.07 15.61 3 18.129"/></svg>
                  {{ doc.languages }}
                </div>
              </div>

              <div class="doctor-card__skills">
                <span v-for="s in doc.skills" :key="s" class="skill-tag">{{ s }}</span>
              </div>

              <NuxtLink to="/appointment" class="btn btn-primary" style="width:100%">
                Book with {{ doc.name.split(' ')[1] }}
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({ title: 'Doctors — DentaCare Premium' })

const doctors = [
  {
    name: 'Dr. Anna Kowalska',
    initials: 'AK',
    specialty: 'Orthodontist',
    experience: 14,
    bio: 'Dr. Kowalska graduated summa cum laude from Warsaw Medical University and completed her orthodontic residency in Berlin. She specializes in complex bite corrections and invisible aligners.',
    days: 'Mon, Wed, Fri',
    languages: 'English, Polish, German',
    skills: ['Clear Aligners', 'Braces', 'Retainers', 'TMJ Therapy'],
    bg: 'linear-gradient(135deg, #dbeafe, #e0f2fe)',
    img: '/images/doctors/anna-kowalska.webp',
  },
  {
    name: 'Dr. Michael Novak',
    initials: 'MN',
    specialty: 'Implantologist',
    experience: 18,
    bio: 'With over 18 years of experience and 3,000+ implants placed, Dr. Novak is one of Warsaw\'s leading implantologists. He trained at the Nobel Biocare Institute in Zürich.',
    days: 'Tue, Thu, Sat',
    languages: 'English, Polish, Czech',
    skills: ['Titanium Implants', 'Bone Grafting', 'All-on-4', 'Sinus Lift'],
    bg: 'linear-gradient(135deg, #d1fae5, #ccfbf1)',
    img: '/images/doctors/michael-novak.jpg',
  },
  {
    name: 'Dr. Sofia Zielinska',
    initials: 'SZ',
    specialty: 'General Dentist',
    experience: 10,
    bio: 'Dr. Zielinska is our patients\' favorite for her warm, pain-free approach to general dentistry. She excels in cosmetic restorations and preventive care for the whole family.',
    days: 'Mon–Fri',
    languages: 'English, Polish, Ukrainian',
    skills: ['Composite Fillings', 'Crowns & Veneers', 'Teeth Whitening', 'Root Canal'],
    bg: 'linear-gradient(135deg, #ede9fe, #fce7f3)',
    img: '/images/doctors/sofia-zielinska.jpeg',
  },
  {
    name: 'Dr. Piotr Wróbel',
    initials: 'PW',
    specialty: 'Oral Surgeon',
    experience: 12,
    bio: 'Dr. Wróbel specializes in complex extractions, jaw surgery, and pre-implant procedures. He completed his surgical fellowship at the University of Vienna.',
    days: 'Tue, Wed, Fri',
    languages: 'English, Polish',
    skills: ['Wisdom Teeth', 'Jaw Surgery', 'Bone Grafts', 'Abscess Treatment'],
    bg: 'linear-gradient(135deg, #fee2e2, #fef3c7)',
    img: '/images/doctors/piotr-wrobel.webp',
  },
  {
    name: 'Dr. Elena Marchetti',
    initials: 'EM',
    specialty: 'Periodontist',
    experience: 9,
    bio: 'Dr. Marchetti focuses on gum health, treating everything from mild gingivitis to advanced periodontitis. She uses laser therapy for minimally invasive gum treatments.',
    days: 'Mon, Thu, Sat',
    languages: 'English, Italian, Polish',
    skills: ['Laser Gum Therapy', 'Deep Cleaning', 'Gum Grafting', 'Implant Maintenance'],
    bg: 'linear-gradient(135deg, #e0f2fe, #ede9fe)',
    img: '/images/doctors/elena-marchetti.jpeg',
  },
  {
    name: 'Dr. Jakub Adamski',
    initials: 'JA',
    specialty: 'Pediatric Dentist',
    experience: 7,
    bio: 'Dr. Adamski has a special talent for making young patients feel safe and comfortable. His gentle approach and fun communication style turn dental visits into positive experiences.',
    days: 'Mon, Tue, Thu',
    languages: 'English, Polish',
    skills: ['Child-Friendly Care', 'Sealants', 'Fluoride Treatment', 'Baby Teeth'],
    bg: 'linear-gradient(135deg, #fef9c3, #d1fae5)',
    img: '/images/doctors/jakub-adamski.avif',
  },
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

.page-hero__inner h1 { font-size: clamp(2rem, 4vw, 3rem); }
.page-hero__inner p { max-width: 500px; color: var(--gray-500); font-size: 1.05rem; }
.page-hero__wave { line-height: 0; }
.page-hero__wave svg { display: block; width: 100%; height: 50px; }

.doctors-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

/* Card */
.doctor-card {
  background: white;
  border-radius: var(--radius-2xl);
  overflow: hidden;
  box-shadow: var(--shadow-md);
  display: flex;
  flex-direction: column;
  transition: transform 0.35s ease, box-shadow 0.35s ease;
}

.doctor-card:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-2xl);
}

/* Photo area */
.doctor-card__photo {
  position: relative;
  height: 280px;
  overflow: hidden;
}

.doctor-card__photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
  display: block;
  transition: transform 0.5s ease;
}

.doctor-card:hover .doctor-card__photo img {
  transform: scale(1.05);
}

/* Gradient overlay at bottom of photo */
.doctor-card__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    transparent 40%,
    rgba(15, 23, 42, 0.7) 100%
  );
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  padding: 1rem 1.1rem;
}

.doctor-card__specialty-pill {
  background: rgb(31 82 220);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.04em;
  padding: 0.35rem 0.875rem;
  border-radius: var(--radius-full);
}

.doctor-card__exp-badge {
  display: flex;
  align-items: center;
  gap: 0.35rem;
  background: rgb(31 82 220);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: white;
  font-size: 0.75rem;
  font-weight: 700;
  padding: 0.35rem 0.75rem;
  border-radius: var(--radius-full);
}

/* Body */
.doctor-card__body {
  padding: 1.5rem 1.75rem 1.75rem;
  display: flex;
  flex-direction: column;
  gap: 0.875rem;
  flex: 1;
}

.doctor-card__body h3 {
  font-family: var(--font-serif);
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--gray-900);
  line-height: 1.25;
}

.doctor-card__bio {
  font-size: 0.875rem;
  color: var(--gray-500);
  line-height: 1.65;
}

/* Meta row */
.doctor-card__meta {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  padding: 0.875rem;
  background: var(--gray-50);
  border-radius: var(--radius-md);
}

.doctor-card__meta-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.82rem;
  color: var(--gray-600);
  font-weight: 500;
}

.doctor-card__meta-item svg {
  color: var(--blue-500);
  flex-shrink: 0;
}

/* Skills */
.doctor-card__skills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-top: auto;
}

.skill-tag {
  padding: 0.3rem 0.7rem;
  background: var(--blue-50);
  border: 1px solid var(--blue-100);
  border-radius: var(--radius-full);
  font-size: 0.73rem;
  font-weight: 600;
  color: var(--blue-700);
}

@media (max-width: 1024px) {
  .doctors-grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 640px) {
  .doctors-grid { grid-template-columns: 1fr; }
  .doctor-card__photo { height: 240px; }
}
</style>
