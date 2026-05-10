<template>
  <div>
    <section class="page-hero gradient-hero">
      <div class="container page-hero__inner">
        <div class="badge badge-blue">Book Appointment</div>
        <h1 class="font-serif">Schedule Your <span class="text-gradient">Visit</span></h1>
        <p>Fill in the form below and our team will confirm your appointment within 2 hours.</p>
      </div>
      <div class="page-hero__wave">
        <svg viewBox="0 0 1440 60" fill="none" preserveAspectRatio="none">
          <path d="M0 60L1440 60L1440 15C1200 60 960 0 720 30C480 60 240 0 0 15L0 60Z" fill="white"/>
        </svg>
      </div>
    </section>

    <section class="section">
      <div class="container appt-layout">

        <!-- Sidebar info -->
        <div class="appt-sidebar">
          <div class="appt-sidebar__card">
            <h3>Appointment Info</h3>
            <div class="appt-info-list">
              <div v-for="item in sidebarInfo" :key="item.label" class="appt-info-item">
                <div class="appt-info-item__icon">{{ item.icon }}</div>
                <div>
                  <div class="appt-info-item__label">{{ item.label }}</div>
                  <div class="appt-info-item__value">{{ item.value }}</div>
                </div>
              </div>
            </div>
          </div>

          <div class="appt-sidebar__card appt-sidebar__emergency">
            <div class="emergency-icon">🚨</div>
            <h4>Dental Emergency?</h4>
            <p>Don't wait. Call our emergency line immediately.</p>
            <a href="tel:+48999111222" class="btn btn-teal" style="width:100%">
              Call: +48 999 111 222
            </a>
          </div>

          <div class="appt-sidebar__card">
            <h3>Why Book With Us?</h3>
            <ul class="appt-perks">
              <li v-for="perk in perks" :key="perk">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg>
                {{ perk }}
              </li>
            </ul>
          </div>
        </div>

        <!-- Form -->
        <div class="appt-form-wrap">
          <!-- Demo notice -->
          <div class="demo-notice">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
            <span><strong>Demo Only</strong> — Currently not connected to a backend. Submissions are simulated. Backend integration not implemented yet.</span>
          </div>

          <!-- Success state -->
          <Transition name="success">
            <div v-if="submitted" class="success-state">
              <div class="success-state__icon">
                <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2.5"><polyline points="20 6 9 17 4 12"/></svg>
              </div>
              <h2 class="font-serif">Appointment Requested!</h2>
              <p>Thank you, <strong>{{ form.fullName }}</strong>! We've received your request and will confirm within 2 hours via email or phone.</p>
              <div class="success-details">
                <div class="success-detail">
                  <span class="success-detail__label">Service:</span>
                  <span>{{ form.service }}</span>
                </div>
                <div class="success-detail">
                  <span class="success-detail__label">Doctor:</span>
                  <span>{{ form.doctor }}</span>
                </div>
                <div class="success-detail">
                  <span class="success-detail__label">Date:</span>
                  <span>{{ form.date }}</span>
                </div>
              </div>
              <button class="btn btn-outline btn-lg" @click="resetForm">Book Another Appointment</button>
            </div>
          </Transition>

          <form v-if="!submitted" class="appt-form" @submit.prevent="handleSubmit" novalidate>
            <h2 class="font-serif appt-form__title">Your Information</h2>

            <div class="form-row">
              <div class="form-group">
                <label class="form-label" for="fullName">Full Name *</label>
                <input
                  id="fullName"
                  v-model="form.fullName"
                  type="text"
                  class="form-input"
                  :class="{ error: errors.fullName }"
                  placeholder="e.g. John Kowalski"
                  @blur="validateField('fullName')"
                />
                <span v-if="errors.fullName" class="form-error">{{ errors.fullName }}</span>
              </div>

              <div class="form-group">
                <label class="form-label" for="email">Email Address *</label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  class="form-input"
                  :class="{ error: errors.email }"
                  placeholder="john@example.com"
                  @blur="validateField('email')"
                />
                <span v-if="errors.email" class="form-error">{{ errors.email }}</span>
              </div>
            </div>

            <div class="form-row">
              <div class="form-group">
                <label class="form-label" for="phone">Phone Number *</label>
                <input
                  id="phone"
                  v-model="form.phone"
                  type="tel"
                  class="form-input"
                  :class="{ error: errors.phone }"
                  placeholder="+48 123 456 789"
                  @blur="validateField('phone')"
                />
                <span v-if="errors.phone" class="form-error">{{ errors.phone }}</span>
              </div>

              <div class="form-group">
                <label class="form-label" for="date">Preferred Date *</label>
                <input
                  id="date"
                  v-model="form.date"
                  type="date"
                  class="form-input"
                  :class="{ error: errors.date }"
                  :min="minDate"
                  @blur="validateField('date')"
                />
                <span v-if="errors.date" class="form-error">{{ errors.date }}</span>
              </div>
            </div>

            <div class="form-row">
              <div class="form-group">
                <label class="form-label" for="service">Service *</label>
                <select
                  id="service"
                  v-model="form.service"
                  class="form-select"
                  :class="{ error: errors.service }"
                  @change="validateField('service')"
                >
                  <option value="">— Select a service —</option>
                  <option v-for="s in serviceOptions" :key="s" :value="s">{{ s }}</option>
                </select>
                <span v-if="errors.service" class="form-error">{{ errors.service }}</span>
              </div>

              <div class="form-group">
                <label class="form-label" for="doctor">Preferred Doctor</label>
                <select id="doctor" v-model="form.doctor" class="form-select">
                  <option value="">— No preference —</option>
                  <option v-for="d in doctorOptions" :key="d" :value="d">{{ d }}</option>
                </select>
              </div>
            </div>

            <div class="form-group">
              <label class="form-label" for="notes">Additional Notes</label>
              <textarea
                id="notes"
                v-model="form.notes"
                class="form-textarea"
                placeholder="Any allergies, previous treatments, or special requests..."
                rows="4"
              ></textarea>
            </div>

            <div class="form-group">
              <label class="form-checkbox">
                <input v-model="form.consent" type="checkbox" :class="{ error: errors.consent }" />
                <span>I agree to the <a href="#" class="link">Privacy Policy</a> and consent to processing of my personal data for appointment scheduling.</span>
              </label>
              <span v-if="errors.consent" class="form-error">{{ errors.consent }}</span>
            </div>

            <button type="submit" class="btn btn-primary btn-lg submit-btn" :class="{ 'submit-btn--loading': loading }" :disabled="loading">
              <span v-if="!loading" class="submit-btn__content">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                Confirm Appointment Request
              </span>
              <span v-else class="submit-btn__content">
                <div class="spinner"></div>
                Sending your request...
              </span>
            </button>
          </form>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({ title: 'Book Appointment — DentaCare Premium' })

const submitted = ref(false)
const loading = ref(false)

const form = reactive({
  fullName: '',
  email: '',
  phone: '',
  date: '',
  service: '',
  doctor: '',
  notes: '',
  consent: false,
})

const errors = reactive({
  fullName: '',
  email: '',
  phone: '',
  date: '',
  service: '',
  consent: '',
})

const minDate = computed(() => {
  const d = new Date()
  d.setDate(d.getDate() + 1)
  return d.toISOString().split('T')[0]
})

const rules = {
  fullName: (v) => !v.trim() ? 'Full name is required.' : v.trim().length < 2 ? 'Name must be at least 2 characters.' : '',
  email: (v) => !v.trim() ? 'Email is required.' : !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v) ? 'Please enter a valid email.' : '',
  phone: (v) => !v.trim() ? 'Phone number is required.' : v.trim().length < 6 ? 'Please enter a valid phone number.' : '',
  date: (v) => !v ? 'Please select a preferred date.' : '',
  service: (v) => !v ? 'Please select a service.' : '',
  consent: (v) => !v ? 'You must agree to the privacy policy.' : '',
}

function validateField(field) {
  errors[field] = rules[field](form[field])
}

function validateAll() {
  let valid = true
  for (const field of Object.keys(rules)) {
    errors[field] = rules[field](form[field])
    if (errors[field]) valid = false
  }
  return valid
}

async function handleSubmit() {
  if (!validateAll()) return
  loading.value = true
  await new Promise(r => setTimeout(r, 1800))
  loading.value = false
  submitted.value = true
}

function resetForm() {
  submitted.value = false
  Object.assign(form, { fullName: '', email: '', phone: '', date: '', service: '', doctor: '', notes: '', consent: false })
  Object.assign(errors, { fullName: '', email: '', phone: '', date: '', service: '', consent: '' })
}

const serviceOptions = [
  'Teeth Cleaning — €50',
  'Caries Treatment — €120',
  'Teeth Whitening — €200',
  'Root Canal Treatment — €250',
  'Orthodontics — from €900',
  'Dental Implants — €1,200',
  'Free Initial Consultation',
  'Other / Not sure',
]

const doctorOptions = [
  'Dr. Anna Kowalska (Orthodontist)',
  'Dr. Michael Novak (Implantologist)',
  'Dr. Sofia Zielinska (General Dentist)',
  'Dr. Piotr Wróbel (Oral Surgeon)',
  'Dr. Elena Marchetti (Periodontist)',
  'Dr. Jakub Adamski (Pediatric Dentist)',
]

const sidebarInfo = [
  { icon: '📍', label: 'Address', value: 'ul. Marszałkowska 140, Warsaw' },
  { icon: '📞', label: 'Phone', value: '+48 123 456 789' },
  { icon: '📧', label: 'Email', value: 'info@dentacare.pl' },
  { icon: '🕐', label: 'Mon–Fri', value: '8:00 – 20:00' },
  { icon: '🕐', label: 'Saturday', value: '9:00 – 15:00' },
  { icon: '❌', label: 'Sunday', value: 'Closed' },
]

const perks = [
  'Free first consultation',
  'Confirmation within 2 hours',
  'Easy rescheduling up to 24h before',
  'No hidden fees',
  'Reminder SMS + email',
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

.appt-layout {
  display: grid;
  grid-template-columns: 320px 1fr;
  gap: 2.5rem;
  align-items: start;
}

/* SIDEBAR */
.appt-sidebar {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  position: sticky;
  top: 6rem;
}

.appt-sidebar__card {
  background: white;
  border-radius: var(--radius-xl);
  padding: 1.75rem;
  box-shadow: var(--shadow-md);
  border: 1px solid var(--gray-100);
}

.appt-sidebar__card h3 {
  font-size: 1rem;
  font-weight: 700;
  color: var(--gray-900);
  margin-bottom: 1.25rem;
}

.appt-info-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.appt-info-item {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
}

.appt-info-item__icon { font-size: 1.25rem; }
.appt-info-item__label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--gray-400); font-weight: 600; }
.appt-info-item__value { font-size: 0.9rem; color: var(--gray-700); font-weight: 500; }

.appt-sidebar__emergency {
  background: linear-gradient(135deg, #f0fdfa, #e0f2fe);
  border-color: var(--blue-200);
  text-align: center;
}

.emergency-icon { font-size: 2rem; margin-bottom: 0.5rem; }
.appt-sidebar__emergency h4 { color: var(--gray-900); font-size: 1rem; margin-bottom: 0.375rem; }
.appt-sidebar__emergency p { color: var(--gray-500); font-size: 0.875rem; margin-bottom: 1rem; }

.appt-perks {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.625rem;
}

.appt-perks li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.875rem;
  color: var(--gray-600);
}

.appt-perks svg { color: var(--teal-500); flex-shrink: 0; }

/* FORM */
.appt-form-wrap {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.demo-notice {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  background: #fff7ed;
  border: 1px solid #fed7aa;
  border-radius: var(--radius-lg);
  padding: 1rem 1.25rem;
  font-size: 0.875rem;
  color: #92400e;
}

.demo-notice svg { color: #ea580c; flex-shrink: 0; margin-top: 2px; }

.appt-form {
  background: white;
  border-radius: var(--radius-2xl);
  padding: 2.5rem;
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--gray-100);
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.appt-form__title {
  font-size: 1.5rem;
  color: var(--gray-900);
  padding-bottom: 1.25rem;
  border-bottom: 2px solid var(--gray-100);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
}

.form-checkbox {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  cursor: pointer;
  font-size: 0.875rem;
  color: var(--gray-600);
  line-height: 1.5;
}

.form-checkbox input {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
  margin-top: 2px;
  accent-color: var(--blue-600);
  cursor: pointer;
}

.link { color: var(--blue-600); text-decoration: underline; }

/* SUBMIT BUTTON */
.submit-btn {
  width: 100%;
  padding: 1.1rem 2rem;
  font-size: 1rem;
  position: relative;
  overflow: hidden;
}

.submit-btn::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, var(--blue-700), var(--teal-600));
  opacity: 0;
  transition: opacity 0.3s;
}

.submit-btn:hover::before { opacity: 1; }

.submit-btn__content {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.625rem;
  position: relative;
}

.submit-btn--loading {
  opacity: 0.9;
  cursor: not-allowed;
}

.spinner {
  width: 18px;
  height: 18px;
  border: 2px solid rgba(255,255,255,0.3);
  border-top-color: white;
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

@keyframes spin { to { transform: rotate(360deg); } }

/* SUCCESS */
.success-enter-active { animation: successIn 0.5s cubic-bezier(0.34, 1.56, 0.64, 1); }

@keyframes successIn {
  from { opacity: 0; transform: scale(0.85) translateY(20px); }
  to { opacity: 1; transform: scale(1) translateY(0); }
}

.success-state {
  background: white;
  border-radius: var(--radius-2xl);
  padding: 3.5rem 2.5rem;
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--gray-100);
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.25rem;
}

.success-state__icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, var(--blue-500), var(--teal-500));
  border-radius: var(--radius-full);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 8px 30px rgb(59 130 246 / 0.4);
  margin-bottom: 0.5rem;
}

.success-state h2 { font-size: 1.75rem; color: var(--gray-900); }
.success-state > p { color: var(--gray-500); font-size: 1rem; max-width: 440px; }

.success-details {
  background: var(--gray-50);
  border-radius: var(--radius-lg);
  padding: 1.25rem 2rem;
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  text-align: left;
}

.success-detail {
  display: flex;
  gap: 1rem;
  font-size: 0.9rem;
}

.success-detail__label { color: var(--gray-400); font-weight: 600; width: 80px; flex-shrink: 0; }
.success-detail span:last-child { color: var(--gray-800); font-weight: 500; }

@media (max-width: 1024px) {
  .appt-layout { grid-template-columns: 1fr; }
  .appt-sidebar { position: static; flex-direction: row; flex-wrap: wrap; }
  .appt-sidebar__card { flex: 1; min-width: 240px; }
}

@media (max-width: 640px) {
  .form-row { grid-template-columns: 1fr; }
  .appt-form { padding: 1.5rem; }
  .appt-sidebar { flex-direction: column; }
}
</style>
