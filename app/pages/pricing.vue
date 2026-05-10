<template>
  <div>
    <section class="page-hero gradient-hero">
      <div class="container page-hero__inner">
        <div class="badge badge-blue">Transparent Pricing</div>
        <h1 class="font-serif">Clear, Honest <span class="text-gradient">Pricing</span></h1>
        <p>No hidden fees, no surprises. All prices include consultation and aftercare advice.</p>
      </div>
      <div class="page-hero__wave">
        <svg viewBox="0 0 1440 60" fill="none" preserveAspectRatio="none">
          <path d="M0 60L1440 60L1440 15C1200 60 960 0 720 30C480 60 240 0 0 15L0 60Z" fill="white"/>
        </svg>
      </div>
    </section>

    <section class="section">
      <div class="container">
        <!-- Category Tabs -->
        <div class="category-tabs">
          <button
            v-for="cat in categories"
            :key="cat.id"
            class="cat-tab"
            :class="{ 'cat-tab--active': activeCategory.value === cat.id }"
            @click="setCategory(cat.id)"
          >
            <span class="cat-tab__icon">{{ cat.icon }}</span>
            {{ cat.label }}
          </button>
        </div>

        <!-- Pricing table -->
        <div v-if="activeCat">
          <div class="pricing-header">
            <div class="pricing-header__icon">{{ activeCat.icon }}</div>
            <div>
              <h2 class="font-serif">{{ activeCat.label }}</h2>
              <p>{{ activeCat.desc }}</p>
            </div>
          </div>

          <div class="pricing-table">
            <div class="pricing-table__head">
              <div>Treatment</div>
              <div>Duration</div>
              <div>Price</div>
              <div>Action</div>
            </div>
            <div
              v-for="item in activeCat.items"
              :key="item.name"
              class="pricing-row"
              :class="{ 'pricing-row--highlight': item.popular }"
            >
              <div class="pricing-row__name">
                <span class="pricing-row__dot" :style="`background: ${activeCat.color}`"></span>
                <div>
                  <div class="pricing-row__title">
                    {{ item.name }}
                    <span v-if="item.popular" class="popular-badge">Most Popular</span>
                  </div>
                  <div class="pricing-row__note">{{ item.note }}</div>
                </div>
              </div>
              <div class="pricing-row__duration">{{ item.duration }}</div>
              <div class="pricing-row__price">{{ item.price }}</div>
              <div>
                <NuxtLink to="/appointment" class="btn btn-primary" style="padding: 0.5rem 1.25rem; font-size: 0.875rem">Book</NuxtLink>
              </div>
            </div>
          </div>
        </div>

        <!-- Notes -->
        <div class="pricing-notes">
          <div class="pricing-notes__inner">
            <div class="pricing-notes__icon">ℹ️</div>
            <div>
              <h4>Pricing Notes</h4>
              <ul>
                <li>All prices are indicative. Final price depends on case complexity assessed during consultation.</li>
                <li>First consultation is always <strong>free of charge</strong>.</li>
                <li>We accept most major insurance plans. Please contact us to confirm coverage.</li>
                <li>Installment plans available for treatments over €300 — interest-free for 12 months.</li>
              </ul>
            </div>
          </div>
        </div>

        <!-- CTA -->
        <div class="pricing-cta gradient-blue">
          <h2 class="font-serif">Get a Personal Quote</h2>
          <p>Book a free consultation and receive an exact treatment plan with full pricing.</p>
          <NuxtLink to="/appointment" class="btn btn-white btn-lg">Book Free Consultation</NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({ title: 'Pricing — DentaCare Premium' })

const activeCategory = ref('prevention')

const activeCat = computed(() => categories.find(c => c.id === activeCategory.value))

function setCategory(id) {
  activeCategory.value = id
}

const categories = [
  {
    id: 'prevention',
    icon: '🛡️',
    label: 'Prevention',
    color: '#3b82f6',
    desc: 'Regular check-ups and preventive care to keep your teeth healthy long-term.',
    items: [
      { name: 'Initial Consultation', note: 'Exam, X-rays, treatment plan', duration: '30 min', price: 'FREE', popular: false },
      { name: 'Teeth Cleaning (Scaling)', note: 'Ultrasonic + polishing', duration: '45 min', price: '€50', popular: true },
      { name: 'Digital X-Ray (1 tooth)', note: 'Instant digital imaging', duration: '10 min', price: '€15', popular: false },
      { name: 'Panoramic X-Ray', note: 'Full jaw imaging', duration: '15 min', price: '€40', popular: false },
      { name: 'Fluoride Treatment', note: 'Strengthens enamel', duration: '20 min', price: '€25', popular: false },
      { name: 'Dental Sealants', note: 'Per tooth, protective coating', duration: '30 min', price: '€30', popular: false },
      { name: 'Caries Treatment (Filling)', note: 'Composite, per tooth', duration: '60 min', price: '€120', popular: false },
    ],
  },
  {
    id: 'surgery',
    icon: '⚕️',
    label: 'Surgery',
    color: '#ea580c',
    desc: 'Surgical treatments performed by our certified oral surgeons with precision and care.',
    items: [
      { name: 'Simple Tooth Extraction', note: 'Under local anesthesia', duration: '30 min', price: '€80', popular: false },
      { name: 'Wisdom Tooth Removal', note: 'Surgical extraction', duration: '60 min', price: '€200', popular: false },
      { name: 'Root Canal Treatment', note: 'Per canal (single root)', duration: '90 min', price: '€250', popular: true },
      { name: 'Root Canal (Multi-root)', note: 'Molars, per tooth', duration: '120 min', price: '€350', popular: false },
      { name: 'Dental Implant (implant only)', note: 'Nobel Biocare titanium', duration: '60 min', price: '€800', popular: false },
      { name: 'Dental Implant (full, incl. crown)', note: 'Implant + abutment + crown', duration: '2 sessions', price: '€1,200', popular: true },
      { name: 'Bone Graft', note: 'For implant preparation', duration: '90 min', price: 'from €400', popular: false },
      { name: 'Sinus Lift', note: 'For upper jaw implants', duration: '2 hrs', price: 'from €600', popular: false },
    ],
  },
  {
    id: 'orthodontics',
    icon: '📐',
    label: 'Orthodontics',
    color: '#16a34a',
    desc: 'Comprehensive teeth alignment treatments for children, teens, and adults.',
    items: [
      { name: 'Orthodontic Consultation', note: 'Assessment + 3D scan', duration: '45 min', price: 'FREE', popular: false },
      { name: 'Metal Braces (full arch)', note: 'Upper or lower', duration: '12–24 months', price: '€900', popular: false },
      { name: 'Ceramic Braces (full arch)', note: 'Tooth-colored brackets', duration: '12–24 months', price: '€1,200', popular: false },
      { name: 'Clear Aligners (Invisalign)', note: 'Full treatment series', duration: '6–18 months', price: 'from €2,500', popular: true },
      { name: 'Clear Aligners (short correction)', note: 'Up to 10 aligners', duration: '3–6 months', price: 'from €900', popular: false },
      { name: 'Fixed Retainer', note: 'Wire bonded to teeth', duration: '30 min', price: '€120', popular: false },
      { name: 'Removable Retainer', note: 'Per arch', duration: '20 min', price: '€80', popular: false },
    ],
  },
  {
    id: 'cosmetic',
    icon: '✨',
    label: 'Cosmetic Dentistry',
    color: '#9333ea',
    desc: 'Aesthetic treatments designed to create the most beautiful, confident smile.',
    items: [
      { name: 'Teeth Whitening (in-office)', note: 'LED activation, 8 shades', duration: '90 min', price: '€200', popular: true },
      { name: 'Teeth Whitening (take-home)', note: 'Custom trays + gel kit', duration: '2 weeks', price: '€120', popular: false },
      { name: 'Composite Veneer (per tooth)', note: 'Same-day, no grinding', duration: '90 min', price: '€150', popular: false },
      { name: 'Porcelain Veneer (per tooth)', note: 'Lab-crafted, 2 sessions', duration: '2 sessions', price: '€450', popular: false },
      { name: 'Full Smile Makeover (6 veneers)', note: 'Upper front teeth', duration: '2–3 sessions', price: 'from €2,400', popular: false },
      { name: 'Zirconia Crown', note: 'Full ceramic, per tooth', duration: '2 sessions', price: '€500', popular: false },
      { name: 'Teeth Contouring', note: 'Reshaping without drilling', duration: '30 min', price: '€60', popular: false },
      { name: 'Gum Contouring (laser)', note: 'Per arch', duration: '45 min', price: '€300', popular: false },
    ],
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

.category-tabs {
  display: flex;
  gap: 0.75rem;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 3rem;
}

.cat-tab {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.625rem 1.5rem;
  border-radius: var(--radius-full);
  border: 2px solid var(--gray-200);
  background: white;
  font-weight: 600;
  font-size: 0.9rem;
  color: var(--gray-600);
  cursor: pointer;
  transition: all 0.25s ease;
}

.cat-tab:hover { border-color: var(--blue-300); color: var(--blue-600); }

.cat-tab--active {
  background: var(--blue-600);
  border-color: var(--blue-600);
  color: white;
  box-shadow: 0 4px 14px rgb(37 99 235 / 0.3);
}

.cat-tab__icon { font-size: 1.1rem; }

.pricing-header {
  display: flex;
  align-items: center;
  gap: 1.25rem;
  margin-bottom: 2rem;
  padding: 1.75rem 2rem;
  background: var(--gray-50);
  border-radius: var(--radius-xl);
  border: 1px solid var(--gray-200);
}

.pricing-header__icon { font-size: 2.5rem; }
.pricing-header h2 { font-size: 1.5rem; margin-bottom: 0.25rem; }
.pricing-header p { color: var(--gray-500); font-size: 0.9rem; }

.pricing-table {
  border-radius: var(--radius-xl);
  overflow: hidden;
  box-shadow: var(--shadow-md);
  border: 1px solid var(--gray-200);
  margin-bottom: 2rem;
}

.pricing-table__head {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 120px;
  gap: 1rem;
  padding: 1rem 1.5rem;
  background: var(--gray-800);
  color: var(--gray-300);
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.pricing-row {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 120px;
  gap: 1rem;
  padding: 1.1rem 1.5rem;
  align-items: center;
  background: white;
  border-bottom: 1px solid var(--gray-100);
  transition: background 0.2s;
}

.pricing-row:last-child { border-bottom: none; }
.pricing-row:hover { background: var(--gray-50); }

.pricing-row--highlight {
  background: var(--blue-50) !important;
  border-left: 3px solid var(--blue-500);
}

.pricing-row__name {
  display: flex;
  align-items: flex-start;
  gap: 0.875rem;
}

.pricing-row__dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin-top: 5px;
  flex-shrink: 0;
}

.pricing-row__title {
  font-weight: 600;
  color: var(--gray-900);
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.pricing-row__note {
  font-size: 0.8rem;
  color: var(--gray-400);
  margin-top: 0.2rem;
}

.popular-badge {
  background: var(--blue-600);
  color: white;
  font-size: 0.7rem;
  padding: 0.15rem 0.5rem;
  border-radius: var(--radius-full);
  font-weight: 700;
}

.pricing-row__duration {
  font-size: 0.875rem;
  color: var(--gray-500);
}

.pricing-row__price {
  font-weight: 800;
  font-size: 1.1rem;
  color: var(--blue-700);
}

.pricing-notes {
  margin-bottom: 3rem;
}

.pricing-notes__inner {
  display: flex;
  gap: 1.25rem;
  background: var(--blue-50);
  border: 1px solid var(--blue-200);
  border-radius: var(--radius-xl);
  padding: 1.5rem 2rem;
}

.pricing-notes__icon { font-size: 1.75rem; flex-shrink: 0; }

.pricing-notes__inner h4 {
  font-weight: 700;
  color: var(--blue-800);
  margin-bottom: 0.625rem;
}

.pricing-notes__inner ul {
  padding-left: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.375rem;
}

.pricing-notes__inner li {
  font-size: 0.875rem;
  color: var(--blue-700);
  line-height: 1.5;
}

.pricing-cta {
  border-radius: var(--radius-2xl);
  padding: 3rem;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.25rem;
}

.pricing-cta h2 { color: white; font-size: 1.75rem; }
.pricing-cta p { color: rgba(255,255,255,0.8); font-size: 1rem; }

@media (max-width: 768px) {
  .pricing-table__head { display: none; }
  .pricing-row {
    grid-template-columns: 1fr;
    gap: 0.5rem;
    padding: 1.25rem 1rem;
  }
  .pricing-row__duration { font-size: 0.8rem; color: var(--gray-400); }
  .pricing-row__price { font-size: 1.25rem; }
}
</style>
