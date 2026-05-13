<template>
  <nav
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-300"
    :class="scrolled ? 'bg-dark-900/80 backdrop-blur-xl border-b border-white/[0.06] shadow-xl' : 'bg-transparent'"
  >
    <div class="container-max px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16 md:h-20">
        <!-- Logo -->
        <router-link to="/" class="flex items-center gap-3 group">
          <div class="w-9 h-9 rounded-lg bg-gradient-to-br from-primary-500 to-accent-500 flex items-center justify-center font-display font-bold text-white text-lg shadow-lg shadow-primary-500/25">
            W
          </div>
          <span class="font-display font-bold text-lg text-white group-hover:text-primary-400 transition-colors">
            Worinium
          </span>
        </router-link>

        <!-- Desktop Menu -->
        <div class="hidden md:flex items-center gap-1">
          <router-link
            v-for="link in navLinks"
            :key="link.to"
            :to="link.to"
            class="px-4 py-2 text-sm font-medium text-gray-300 hover:text-white rounded-lg hover:bg-white/[0.05] transition-all duration-200"
            active-class="!text-primary-400 bg-primary-500/10"
          >
            {{ link.label }}
          </router-link>
          <router-link to="/contact" class="btn-primary ml-4 text-sm px-5 py-2.5">
            Get Started
          </router-link>
        </div>

        <!-- Mobile Toggle -->
        <button
          @click="mobileOpen = !mobileOpen"
          class="md:hidden p-2 rounded-lg text-gray-400 hover:text-white hover:bg-white/[0.05] transition-colors"
          :aria-label="mobileOpen ? 'Close menu' : 'Open menu'"
        >
          <svg v-if="!mobileOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
          <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="opacity-0 -translate-y-2"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 -translate-y-2"
      >
        <div v-if="mobileOpen" class="md:hidden pb-4 border-t border-white/[0.06] mt-2 pt-4">
          <router-link
            v-for="link in navLinks"
            :key="link.to"
            :to="link.to"
            @click="mobileOpen = false"
            class="block px-4 py-3 text-sm font-medium text-gray-300 hover:text-white rounded-lg hover:bg-white/[0.05] transition-colors"
            active-class="!text-primary-400 bg-primary-500/10"
          >
            {{ link.label }}
          </router-link>
          <router-link to="/contact" @click="mobileOpen = false" class="btn-primary mt-3 w-full text-sm">
            Get Started
          </router-link>
        </div>
      </transition>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const mobileOpen = ref(false)

const navLinks = [
  { label: 'Home', to: '/' },
  { label: 'Solutions', to: '/solutions' },
  { label: 'About', to: '/about' },
  { label: 'Contact', to: '/contact' }
]

function onScroll() {
  scrolled.value = window.scrollY > 20
}

onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>
