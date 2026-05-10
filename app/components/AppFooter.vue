<template>
  <footer class="footer">
    <div class="footer__top">
      <div class="container footer__grid">
        <div class="footer__brand">
          <div class="footer__logo">
            <div class="logo-icon-sm">
               <img width="35" height="35" src="/images/tooth.png" alt="DentaCare Premium" />
            </div>
            <span>DentaCare <b>Premium</b></span>
          </div>
          <p class="footer__tagline">Your healthy smile is our mission. Premium dental care with compassionate service since 2010.</p>
          <div class="footer__social">
            <a href="#" class="social-link" aria-label="Facebook">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z"/></svg>
            </a>
            <a href="#" class="social-link" aria-label="Instagram">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
            </a>
            <a href="#" class="social-link" aria-label="LinkedIn">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 016 6v7h-4v-7a2 2 0 00-2-2 2 2 0 00-2 2v7h-4v-7a6 6 0 016-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
            </a>
          </div>
        </div>

        <div class="footer__col">
          <h4>Services</h4>
          <ul>
            <li><NuxtLink to="/services">Teeth Cleaning</NuxtLink></li>
            <li><NuxtLink to="/services">Caries Treatment</NuxtLink></li>
            <li><NuxtLink to="/services">Teeth Whitening</NuxtLink></li>
            <li><NuxtLink to="/services">Dental Implants</NuxtLink></li>
            <li><NuxtLink to="/services">Orthodontics</NuxtLink></li>
            <li><NuxtLink to="/services">Root Canal</NuxtLink></li>
          </ul>
        </div>

        <div class="footer__col">
          <h4>Clinic</h4>
          <ul>
            <li><NuxtLink to="/doctors">Our Doctors</NuxtLink></li>
            <li><NuxtLink to="/pricing">Pricing</NuxtLink></li>
            <li><NuxtLink to="/appointment">Book Appointment</NuxtLink></li>
            <li><a href="#">About Us</a></li>
            <li><a href="#">Blog</a></li>
            <li><a href="#">Contact</a></li>
          </ul>
        </div>

        <div class="footer__col">
          <h4>Contact</h4>
          <ul class="contact-list">
            <li>
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
              ul. Marszałkowska 140, Warsaw
            </li>
            <li>
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81"/></svg>
              +48 123 456 789
            </li>
            <li>
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
              info@dentacare.pl
            </li>
            <li>
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>
              Mon–Fri: 8:00–20:00<br>Sat: 9:00–15:00
            </li>
          </ul>
        </div>
      </div>
    </div>

    <div class="footer__bottom">
      <div class="container footer__bottom-inner">
        <p>&copy; 2026 DentaCare Premium. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--gray-900);
  color: var(--gray-300);
}

.footer__top {
  padding: 4rem 0 3rem;
}

.footer__grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1.5fr;
  gap: 3rem;
}

.footer__logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.1rem;
  font-weight: 600;
  color: white;
  margin-bottom: 1rem;
}

.logo-icon-sm {
  width: 34px;
  height: 34px;
  background: linear-gradient(135deg, var(--blue-600), var(--teal-500));
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.footer__tagline {
  font-size: 0.9rem;
  line-height: 1.7;
  color: var(--gray-400);
  margin-bottom: 1.5rem;
}

.footer__social {
  display: flex;
  gap: 0.625rem;
}

.social-link {
  width: 38px;
  height: 38px;
  border-radius: 10px;
  background: var(--gray-800);
  color: var(--gray-400);
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all 0.2s;
}

.social-link:hover {
  background: var(--blue-600);
  color: white;
  transform: translateY(-2px);
}

.footer__col h4 {
  color: white;
  font-size: 0.95rem;
  font-weight: 700;
  margin-bottom: 1.25rem;
  letter-spacing: 0.025em;
}

.footer__col ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.625rem;
}

.footer__col ul li a,
.footer__col ul li {
  color: var(--gray-400);
  text-decoration: none;
  font-size: 0.9rem;
  transition: color 0.2s;
  display: flex;
  align-items: flex-start;
  gap: 0.5rem;
}

.footer__col ul li a:hover { color: var(--blue-400); }

.contact-list li svg { flex-shrink: 0; margin-top: 2px; color: var(--blue-400); }

.footer__bottom {
  border-top: 1px solid var(--gray-800);
  padding: 1.25rem 0;
}

.footer__bottom-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer__bottom p {
  font-size: 0.875rem;
  color: var(--gray-500);
}

@media (max-width: 1024px) {
  .footer__grid { grid-template-columns: 1fr 1fr; }
  .footer__brand { grid-column: 1 / -1; }
}

@media (max-width: 640px) {
  .footer__grid { grid-template-columns: 1fr; gap: 2rem; }
  .footer__bottom-inner { flex-direction: column; text-align: center; }
}
</style>
