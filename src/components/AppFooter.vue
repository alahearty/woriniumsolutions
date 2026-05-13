<template>
  <footer class="border-t border-white/[0.06] bg-dark-950">
    <div class="container-max section-padding !py-12 md:!py-16">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10 lg:gap-8">
        <!-- Brand -->
        <div class="lg:col-span-1">
          <router-link to="/" class="flex items-center gap-3 mb-4">
            <div class="w-9 h-9 rounded-lg bg-gradient-to-br from-primary-500 to-accent-500 flex items-center justify-center font-display font-bold text-white text-lg">
              W
            </div>
            <span class="font-display font-bold text-lg text-white">Worinium</span>
          </router-link>
          <p class="text-sm text-gray-500 leading-relaxed">
            Enterprise software solutions powering the Oil & Gas industry, government agencies, and industrial operations.
          </p>
        </div>

        <!-- Solutions -->
        <div>
          <h4 class="text-sm font-semibold text-white mb-4">Solutions</h4>
          <ul class="space-y-2.5">
            <li v-for="item in solutions" :key="item">
              <router-link to="/solutions" class="text-sm text-gray-500 hover:text-primary-400 transition-colors">
                {{ item }}
              </router-link>
            </li>
          </ul>
        </div>

        <!-- Company -->
        <div>
          <h4 class="text-sm font-semibold text-white mb-4">Company</h4>
          <ul class="space-y-2.5">
            <li v-for="link in companyLinks" :key="link.to">
              <router-link :to="link.to" class="text-sm text-gray-500 hover:text-primary-400 transition-colors">
                {{ link.label }}
              </router-link>
            </li>
          </ul>
        </div>

        <!-- Contact -->
        <div>
          <h4 class="text-sm font-semibold text-white mb-4">Contact</h4>
          <ul class="space-y-2.5 text-sm text-gray-500">
            <li class="flex items-start gap-2">
              <svg class="w-4 h-4 mt-0.5 text-primary-500 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
              </svg>
              <a href="mailto:info@woriniumsolutions.com" class="hover:text-primary-400 transition-colors">
                info@woriniumsolutions.com
              </a>
            </li>
            <li class="flex items-start gap-2">
              <svg class="w-4 h-4 mt-0.5 text-primary-500 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
              <span>Enterprise Solutions Worldwide</span>
            </li>
          </ul>
        </div>
      </div>

      <div class="border-t border-white/[0.06] mt-12 pt-8 flex flex-col md:flex-row items-center justify-between gap-4">
        <p class="text-xs text-gray-600">
          &copy; {{ new Date().getFullYear() }} Worinium Solutions. All rights reserved.
        </p>
        <div class="flex items-center gap-6">
          <a href="#" class="text-xs text-gray-600 hover:text-gray-400 transition-colors">Privacy Policy</a>
          <a href="#" class="text-xs text-gray-600 hover:text-gray-400 transition-colors">Terms of Service</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const solutions = [
  'Well Integrity (WIMS)',
  'Production Management',
  'GIS & Mapping',
  'Workflow Automation',
  'Custom Development'
]

const companyLinks = [
  { label: 'About Us', to: '/about' },
  { label: 'Solutions', to: '/solutions' },
  { label: 'Contact', to: '/contact' }
]
</script>
