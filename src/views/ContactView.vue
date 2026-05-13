<template>
  <div>
    <!-- Hero -->
    <section class="relative pt-32 pb-16 md:pt-40 md:pb-24 overflow-hidden">
      <div class="absolute inset-0">
        <div class="absolute top-1/3 -right-32 w-96 h-96 bg-primary-600/15 rounded-full blur-[128px]"></div>
        <div class="absolute bottom-0 -left-32 w-80 h-80 bg-accent-600/10 rounded-full blur-[128px]"></div>
        <div class="absolute inset-0 bg-[linear-gradient(rgba(255,255,255,0.015)_1px,transparent_1px),linear-gradient(90deg,rgba(255,255,255,0.015)_1px,transparent_1px)] bg-[size:60px_60px]"></div>
      </div>

      <div class="container-max px-4 sm:px-6 lg:px-8 relative z-10">
        <span class="section-label">Contact Us</span>
        <h1 class="section-title max-w-3xl">
          Let's Build Something <span class="gradient-text">Extraordinary</span>
        </h1>
        <p class="section-subtitle max-w-2xl mt-4">
          Whether you need a custom enterprise solution or want to explore our existing products, we'd love to hear from you.
        </p>
      </div>
    </section>

    <!-- Contact Content -->
    <section class="section-padding !pt-0">
      <div class="container-max">
        <div class="grid grid-cols-1 lg:grid-cols-5 gap-8">
          <!-- Form -->
          <div class="lg:col-span-3">
            <div class="glass-card p-6 md:p-8">
              <h2 class="text-lg font-display font-bold text-white mb-6">Send Us a Message</h2>

              <form @submit.prevent="handleSubmit" class="space-y-5">
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                  <div>
                    <label for="name" class="block text-xs font-medium text-gray-400 mb-2 uppercase tracking-wider">Full Name</label>
                    <input
                      id="name"
                      v-model="form.name"
                      type="text"
                      required
                      class="w-full px-4 py-3 rounded-lg bg-white/[0.03] border border-white/[0.08] text-white text-sm
                             placeholder-gray-600 focus:outline-none focus:border-primary-500/50 focus:ring-1 focus:ring-primary-500/25
                             transition-colors"
                      placeholder="John Doe"
                    />
                  </div>
                  <div>
                    <label for="email" class="block text-xs font-medium text-gray-400 mb-2 uppercase tracking-wider">Email Address</label>
                    <input
                      id="email"
                      v-model="form.email"
                      type="email"
                      required
                      class="w-full px-4 py-3 rounded-lg bg-white/[0.03] border border-white/[0.08] text-white text-sm
                             placeholder-gray-600 focus:outline-none focus:border-primary-500/50 focus:ring-1 focus:ring-primary-500/25
                             transition-colors"
                      placeholder="john@company.com"
                    />
                  </div>
                </div>

                <div>
                  <label for="company" class="block text-xs font-medium text-gray-400 mb-2 uppercase tracking-wider">Company / Organization</label>
                  <input
                    id="company"
                    v-model="form.company"
                    type="text"
                    class="w-full px-4 py-3 rounded-lg bg-white/[0.03] border border-white/[0.08] text-white text-sm
                           placeholder-gray-600 focus:outline-none focus:border-primary-500/50 focus:ring-1 focus:ring-primary-500/25
                           transition-colors"
                    placeholder="Acme Corp"
                  />
                </div>

                <div>
                  <label for="interest" class="block text-xs font-medium text-gray-400 mb-2 uppercase tracking-wider">I'm Interested In</label>
                  <select
                    id="interest"
                    v-model="form.interest"
                    class="w-full px-4 py-3 rounded-lg bg-white/[0.03] border border-white/[0.08] text-white text-sm
                           focus:outline-none focus:border-primary-500/50 focus:ring-1 focus:ring-primary-500/25
                           transition-colors appearance-none"
                  >
                    <option value="" disabled class="bg-dark-900">Select a service...</option>
                    <option v-for="opt in interestOptions" :key="opt" :value="opt" class="bg-dark-900">{{ opt }}</option>
                  </select>
                </div>

                <div>
                  <label for="message" class="block text-xs font-medium text-gray-400 mb-2 uppercase tracking-wider">Message</label>
                  <textarea
                    id="message"
                    v-model="form.message"
                    rows="5"
                    required
                    class="w-full px-4 py-3 rounded-lg bg-white/[0.03] border border-white/[0.08] text-white text-sm
                           placeholder-gray-600 focus:outline-none focus:border-primary-500/50 focus:ring-1 focus:ring-primary-500/25
                           transition-colors resize-none"
                    placeholder="Tell us about your project or requirements..."
                  ></textarea>
                </div>

                <button type="submit" class="btn-primary w-full sm:w-auto" :disabled="submitted">
                  <span v-if="!submitted">Send Message</span>
                  <span v-else class="flex items-center gap-2">
                    <svg class="w-4 h-4 text-green-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                    </svg>
                    Message Sent
                  </span>
                </button>
              </form>
            </div>
          </div>

          <!-- Sidebar -->
          <div class="lg:col-span-2 space-y-6">
            <!-- Contact Info -->
            <div class="glass-card p-6">
              <h3 class="text-white font-semibold mb-5">Get In Touch</h3>
              <div class="space-y-4">
                <div v-for="info in contactInfo" :key="info.label" class="flex items-start gap-3">
                  <div class="w-9 h-9 rounded-lg bg-primary-500/10 border border-primary-500/20 flex items-center justify-center shrink-0">
                    <span class="text-sm" v-html="info.icon"></span>
                  </div>
                  <div>
                    <div class="text-xs text-gray-500 uppercase tracking-wider mb-0.5">{{ info.label }}</div>
                    <div class="text-sm text-gray-300">{{ info.value }}</div>
                  </div>
                </div>
              </div>
            </div>

            <!-- What to expect -->
            <div class="glass-card p-6">
              <h3 class="text-white font-semibold mb-5">What to Expect</h3>
              <div class="space-y-4">
                <div v-for="(step, i) in steps" :key="step" class="flex items-start gap-3">
                  <div class="w-7 h-7 rounded-full bg-primary-500/10 border border-primary-500/20 flex items-center justify-center shrink-0">
                    <span class="text-xs font-bold text-primary-400">{{ i + 1 }}</span>
                  </div>
                  <p class="text-sm text-gray-400 pt-0.5">{{ step }}</p>
                </div>
              </div>
            </div>

            <!-- Industries -->
            <div class="glass-card p-6">
              <h3 class="text-white font-semibold mb-4">Industries We Serve</h3>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="ind in industries"
                  :key="ind"
                  class="px-3 py-1.5 text-xs rounded-full bg-white/[0.04] text-gray-400 border border-white/[0.06]"
                >
                  {{ ind }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({
  name: '',
  email: '',
  company: '',
  interest: '',
  message: ''
})

const submitted = ref(false)

const interestOptions = [
  'Well Integrity Management (WIMS)',
  'Production & Operations Management',
  'GIS & Geospatial Mapping',
  'Enterprise Workflow & Reporting',
  'Custom Software Development',
  'Software Licensing / SaaS',
  'Maintenance & Support',
  'Consulting & Technical Support'
]

function handleSubmit() {
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    form.name = ''
    form.email = ''
    form.company = ''
    form.interest = ''
    form.message = ''
  }, 3000)
}

const contactInfo = [
  { label: 'Email', value: 'info@woriniumsolutions.com', icon: '&#9993;' },
  { label: 'Location', value: 'Enterprise Solutions Worldwide', icon: '&#127760;' },
  { label: 'Support', value: 'Available 24/7', icon: '&#128222;' }
]

const steps = [
  'We review your inquiry within 24 hours',
  'A specialist schedules a discovery call',
  'We present a tailored solution proposal',
  'Development begins upon agreement'
]

const industries = [
  'Oil & Gas',
  'Energy & Utilities',
  'Government',
  'Engineering',
  'Industrial Operations',
  'Enterprise'
]
</script>
