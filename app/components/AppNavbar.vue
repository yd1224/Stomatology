<template>
  <header :class="['navbar', { 'navbar--scrolled': scrolled, 'navbar--open': menuOpen }]">
    <div class="container navbar__inner">
      <NuxtLink to="/" class="navbar__logo">
        <div class="logo-icon">
          <img width="35" height="35" src="/images/tooth.png" alt="DentaCare Premium" />
        </div>
        <span class="logo-text">DentaCare <span>Premium</span></span>
      </NuxtLink>

      <nav class="navbar__nav">
        <NuxtLink to="/" class="nav-link">Home</NuxtLink>
        <NuxtLink to="/services" class="nav-link">Services</NuxtLink>
        <NuxtLink to="/doctors" class="nav-link">Doctors</NuxtLink>
        <NuxtLink to="/pricing" class="nav-link">Pricing</NuxtLink>
        <NuxtLink to="/appointment" class="nav-link">Appointment</NuxtLink>
      </nav>

      <div class="navbar__actions">
        <a href="tel:+48123456789" class="phone-link">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
            <path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07A19.5 19.5 0 013.07 9.81a19.79 19.79 0 01-3.07-8.63A2 2 0 012 0h3a2 2 0 012 1.72c.127.96.361 1.903.7 2.81a2 2 0 01-.45 2.11L6.09 7.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0122 16.92z"/>
          </svg>
          +48 123 456 789
        </a>
        <NuxtLink to="/appointment" class="btn btn-primary">Book Now</NuxtLink>
      </div>

      <button class="hamburger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen">
        <span></span><span></span><span></span>
      </button>
    </div>

    <div class="mobile-menu" :class="{ 'mobile-menu--open': menuOpen }">
      <nav class="mobile-nav">
        <NuxtLink to="/" class="mobile-nav__link" @click="menuOpen = false">Home</NuxtLink>
        <NuxtLink to="/services" class="mobile-nav__link" @click="menuOpen = false">Services</NuxtLink>
        <NuxtLink to="/doctors" class="mobile-nav__link" @click="menuOpen = false">Doctors</NuxtLink>
        <NuxtLink to="/pricing" class="mobile-nav__link" @click="menuOpen = false">Pricing</NuxtLink>
        <NuxtLink to="/appointment" class="mobile-nav__link" @click="menuOpen = false">Appointment</NuxtLink>
      </nav>
      <div class="mobile-menu__footer">
        <a href="tel:+48123456789" class="btn btn-outline" style="width:100%">Call Us: +48 123 456 789</a>
        <NuxtLink to="/appointment" class="btn btn-primary" style="width:100%" @click="menuOpen = false">Book Appointment</NuxtLink>
      </div>
    </div>
  </header>
</template>

<script setup>
const scrolled = ref(false)
const menuOpen = ref(false)

onMounted(() => {
  const handleScroll = () => { scrolled.value = window.scrollY > 20 }
  window.addEventListener('scroll', handleScroll, { passive: true })
  onUnmounted(() => window.removeEventListener('scroll', handleScroll))
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  transition: all 0.3s ease;
  padding: 1.25rem 0;
}

.navbar--scrolled {
  background: rgba(255, 255, 255, 0.97);
  backdrop-filter: blur(20px);
  box-shadow: 0 1px 20px rgb(0 0 0 / 0.08);
  padding: 0.75rem 0;
}

.navbar__inner {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.navbar__logo {
  display: flex;
  align-items: center;
  gap: 0.625rem;
  text-decoration: none;
  flex-shrink: 0;
}

.logo-icon {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, #eff6ff, #e0f2fe);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 8px rgb(59 130 246 / 0.2);
}

.logo-text {
  font-weight: 700;
  font-size: 1.1rem;
  color: var(--gray-900);
}

.logo-text span {
  color: var(--blue-600);
}

.navbar__nav {
  display: flex;
  align-items: center;
  gap: 0.25rem;
  margin: 0 auto;
}

.nav-link {
  padding: 0.5rem 0.875rem;
  border-radius: var(--radius-full);
  text-decoration: none;
  font-weight: 500;
  font-size: 0.9rem;
  color: var(--gray-600);
  transition: all 0.2s ease;
}

.nav-link:hover,
.nav-link.router-link-active {
  color: var(--blue-600);
  background: var(--blue-50);
}

.navbar__actions {
  display: flex;
  align-items: center;
  gap: 1rem;
  flex-shrink: 0;
}

.phone-link {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  color: var(--gray-600);
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 500;
  transition: color 0.2s;
}

.phone-link:hover { color: var(--blue-600); }

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  margin-left: auto;
}

.hamburger span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--gray-700);
  border-radius: 2px;
  transition: all 0.3s ease;
}

.navbar--open .hamburger span:nth-child(1) { transform: rotate(45deg) translate(5px, 5px); }
.navbar--open .hamburger span:nth-child(2) { opacity: 0; }
.navbar--open .hamburger span:nth-child(3) { transform: rotate(-45deg) translate(5px, -5px); }

.mobile-menu {
  display: none;
  background: white;
  padding: 0 1rem;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s ease, padding 0.3s ease;
}

.mobile-menu--open {
  max-height: 500px;
  padding: 1rem;
}

.mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  margin-bottom: 1rem;
}

.mobile-nav__link {
  padding: 0.75rem 1rem;
  border-radius: var(--radius-md);
  text-decoration: none;
  font-weight: 500;
  color: var(--gray-700);
  transition: all 0.2s;
}

.mobile-nav__link:hover,
.mobile-nav__link.router-link-active {
  background: var(--blue-50);
  color: var(--blue-600);
}

.mobile-menu__footer {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  padding-top: 1rem;
  border-top: 1px solid var(--gray-100);
}

@media (max-width: 768px) {
  .navbar__nav, .navbar__actions { display: none; }
  .hamburger { display: flex; }
  .mobile-menu { display: block; }
  .navbar--scrolled { padding-bottom: 0; }
}
</style>
