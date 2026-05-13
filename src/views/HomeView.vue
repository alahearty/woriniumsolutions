<template>
  <div>
    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center overflow-hidden">
      <!-- Background effects -->
      <div class="absolute inset-0">
        <div class="absolute top-1/4 -left-32 w-96 h-96 bg-primary-600/20 rounded-full blur-[128px] animate-float"></div>
        <div class="absolute bottom-1/4 -right-32 w-96 h-96 bg-accent-600/15 rounded-full blur-[128px] animate-float animation-delay-400"></div>
        <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-primary-800/10 rounded-full blur-[200px]"></div>
        <!-- Grid pattern -->
        <div class="absolute inset-0 bg-[linear-gradient(rgba(255,255,255,0.02)_1px,transparent_1px),linear-gradient(90deg,rgba(255,255,255,0.02)_1px,transparent_1px)] bg-[size:60px_60px]"></div>
      </div>

      <div class="container-max px-4 sm:px-6 lg:px-8 relative z-10 pt-24 pb-16">
        <div class="max-w-4xl">
          <div class="animate-fade-in-up">
            <span class="section-label">Enterprise Software Solutions</span>
          </div>

          <h1 class="animate-fade-in-up animation-delay-200 text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-display font-bold text-white leading-[1.1] mt-4">
            Powering the
            <span class="gradient-text"> Oil & Gas</span>
            Industry with
            <span class="gradient-text">Intelligent Software</span>
          </h1>

          <p class="animate-fade-in-up animation-delay-400 text-lg md:text-xl text-gray-400 mt-6 max-w-2xl leading-relaxed">
            Custom-built web and desktop applications for operational management, asset monitoring, geospatial visualization, and workflow automation.
          </p>

          <div class="animate-fade-in-up animation-delay-600 flex flex-wrap gap-4 mt-10">
            <router-link to="/solutions" class="btn-primary text-base px-8 py-4">
              Explore Solutions
              <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </router-link>
            <router-link to="/contact" class="btn-secondary text-base px-8 py-4">
              Contact Us
            </router-link>
          </div>

          <!-- Stats -->
          <div class="animate-fade-in-up animation-delay-800 grid grid-cols-3 gap-8 mt-16 max-w-lg">
            <div v-for="stat in heroStats" :key="stat.label">
              <div class="text-2xl md:text-3xl font-display font-bold text-white">{{ stat.value }}</div>
              <div class="text-xs text-gray-500 mt-1 uppercase tracking-wider">{{ stat.label }}</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Scroll indicator -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-gray-600">
        <span class="text-[10px] uppercase tracking-[0.2em]">Scroll</span>
        <div class="w-5 h-8 rounded-full border border-gray-700 flex items-start justify-center p-1">
          <div class="w-1 h-2 bg-gray-600 rounded-full animate-bounce"></div>
        </div>
      </div>
    </section>

    <!-- Industries Section -->
    <section class="section-padding border-t border-white/[0.04]">
      <div class="container-max">
        <div class="text-center mb-16">
          <span class="section-label">Who We Serve</span>
          <h2 class="section-title">Industries We <span class="gradient-text">Transform</span></h2>
          <p class="section-subtitle mx-auto">
            Delivering mission-critical software to organizations that demand reliability, security, and performance.
          </p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          <div
            v-for="industry in industries"
            :key="industry.title"
            class="glass-card-hover p-6 text-center group"
          >
            <div class="w-14 h-14 mx-auto mb-4 rounded-xl bg-gradient-to-br flex items-center justify-center text-2xl"
              :class="industry.gradient"
            >
              <span v-html="industry.icon"></span>
            </div>
            <h3 class="text-white font-semibold mb-2">{{ industry.title }}</h3>
            <p class="text-sm text-gray-500 leading-relaxed">{{ industry.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Solutions Overview -->
    <section class="section-padding bg-dark-900/50">
      <div class="container-max">
        <div class="text-center mb-16">
          <span class="section-label">Our Solutions</span>
          <h2 class="section-title">Enterprise-Grade <span class="gradient-text">Products</span></h2>
          <p class="section-subtitle mx-auto">
            Purpose-built platforms designed for the unique challenges of energy, government, and industrial operations.
          </p>
        </div>

        <div class="space-y-6">
          <div
            v-for="(solution, index) in solutions"
            :key="solution.title"
            class="glass-card-hover p-6 md:p-8 flex flex-col md:flex-row gap-6 items-start"
          >
            <div class="w-12 h-12 rounded-xl shrink-0 flex items-center justify-center text-xl"
              :class="solution.iconBg"
            >
              <span v-html="solution.icon"></span>
            </div>
            <div class="flex-1">
              <div class="flex items-center gap-3 mb-2">
                <span class="text-[10px] font-bold tracking-[0.2em] uppercase text-primary-500">{{ String(index + 1).padStart(2, '0') }}</span>
                <h3 class="text-lg font-display font-bold text-white">{{ solution.title }}</h3>
              </div>
              <p class="text-gray-400 leading-relaxed">{{ solution.description }}</p>
              <div class="flex flex-wrap gap-2 mt-4">
                <span
                  v-for="tag in solution.tags"
                  :key="tag"
                  class="px-3 py-1 text-xs rounded-full bg-white/[0.04] text-gray-400 border border-white/[0.06]"
                >
                  {{ tag }}
                </span>
              </div>
            </div>
          </div>
        </div>

        <div class="text-center mt-12">
          <router-link to="/solutions" class="btn-primary">
            View All Solutions
            <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3" />
            </svg>
          </router-link>
        </div>
      </div>
    </section>

    <!-- Why Worinium -->
    <section class="section-padding">
      <div class="container-max">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
          <div>
            <span class="section-label">Why Worinium</span>
            <h2 class="section-title">Built for <span class="gradient-text">Mission-Critical</span> Operations</h2>
            <p class="section-subtitle">
              We understand the unique demands of the energy sector and government operations. Our solutions are engineered for reliability, compliance, and scale.
            </p>

            <div class="space-y-6 mt-10">
              <div v-for="item in whyItems" :key="item.title" class="flex gap-4">
                <div class="w-10 h-10 rounded-lg bg-primary-500/10 border border-primary-500/20 flex items-center justify-center shrink-0">
                  <svg class="w-5 h-5 text-primary-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                  </svg>
                </div>
                <div>
                  <h4 class="text-white font-semibold mb-1">{{ item.title }}</h4>
                  <p class="text-sm text-gray-500 leading-relaxed">{{ item.desc }}</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Visual -->
          <div class="relative">
            <div class="glass-card p-8 relative z-10">
              <div class="space-y-4">
                <div class="flex items-center gap-3 pb-4 border-b border-white/[0.06]">
                  <div class="w-3 h-3 rounded-full bg-red-500/80"></div>
                  <div class="w-3 h-3 rounded-full bg-yellow-500/80"></div>
                  <div class="w-3 h-3 rounded-full bg-green-500/80"></div>
                  <span class="text-xs text-gray-600 ml-2">worinium-dashboard.app</span>
                </div>
                <div class="grid grid-cols-2 gap-3">
                  <div class="glass-card p-4 rounded-xl">
                    <div class="text-xs text-gray-500 mb-1">Active Wells</div>
                    <div class="text-xl font-display font-bold text-primary-400">2,847</div>
                    <div class="text-[10px] text-green-400 mt-1">+12.4% this month</div>
                  </div>
                  <div class="glass-card p-4 rounded-xl">
                    <div class="text-xs text-gray-500 mb-1">Risk Score</div>
                    <div class="text-xl font-display font-bold text-green-400">Low</div>
                    <div class="text-[10px] text-gray-500 mt-1">98.2% compliance</div>
                  </div>
                  <div class="glass-card p-4 rounded-xl">
                    <div class="text-xs text-gray-500 mb-1">Inspections</div>
                    <div class="text-xl font-display font-bold text-accent-400">1,203</div>
                    <div class="text-[10px] text-gray-500 mt-1">This quarter</div>
                  </div>
                  <div class="glass-card p-4 rounded-xl">
                    <div class="text-xs text-gray-500 mb-1">Uptime</div>
                    <div class="text-xl font-display font-bold text-white">99.9%</div>
                    <div class="text-[10px] text-gray-500 mt-1">Last 90 days</div>
                  </div>
                </div>
                <div class="glass-card p-4 rounded-xl">
                  <div class="text-xs text-gray-500 mb-3">Production Output (BBL/day)</div>
                  <div class="flex items-end gap-1 h-16">
                    <div v-for="(h, i) in barHeights" :key="i"
                      class="flex-1 rounded-t bg-gradient-to-t from-primary-600 to-primary-400 opacity-80"
                      :style="{ height: h + '%' }"
                    ></div>
                  </div>
                </div>
              </div>
            </div>
            <div class="absolute -top-4 -right-4 w-full h-full rounded-2xl bg-gradient-to-br from-primary-600/20 to-accent-600/20 blur-xl -z-10"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="section-padding">
      <div class="container-max">
        <div class="relative glass-card p-8 md:p-16 text-center overflow-hidden">
          <div class="absolute top-0 left-1/2 -translate-x-1/2 w-96 h-48 bg-primary-600/20 rounded-full blur-[100px]"></div>
          <div class="relative z-10">
            <span class="section-label">Get Started</span>
            <h2 class="section-title mt-2">Ready to Transform Your <span class="gradient-text">Operations</span>?</h2>
            <p class="section-subtitle mx-auto mt-4">
              Let's discuss how Worinium Solutions can help modernize your enterprise with custom-built, industry-specific software.
            </p>
            <div class="flex flex-wrap justify-center gap-4 mt-10">
              <router-link to="/contact" class="btn-primary text-base px-8 py-4">
                Schedule a Consultation
              </router-link>
              <router-link to="/solutions" class="btn-secondary text-base px-8 py-4">
                Explore Solutions
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const heroStats = [
  { value: '50+', label: 'Projects' },
  { value: '99.9%', label: 'Uptime' },
  { value: '24/7', label: 'Support' }
]

const industries = [
  {
    title: 'Oil & Gas',
    desc: 'Well integrity, production tracking, and operational management systems.',
    icon: '&#9951;',
    gradient: 'from-primary-500/20 to-primary-700/20 text-primary-400'
  },
  {
    title: 'Energy & Utilities',
    desc: 'Asset monitoring, performance analytics, and infrastructure management.',
    icon: '&#9889;',
    gradient: 'from-yellow-500/20 to-yellow-700/20 text-yellow-400'
  },
  {
    title: 'Government',
    desc: 'Workflow automation, reporting, and secure data management platforms.',
    icon: '&#127963;',
    gradient: 'from-accent-500/20 to-accent-700/20 text-accent-400'
  },
  {
    title: 'Industrial',
    desc: 'Enterprise software for engineering firms and industrial operations.',
    icon: '&#9881;',
    gradient: 'from-green-500/20 to-green-700/20 text-green-400'
  }
]

const solutions = [
  {
    title: 'Well Integrity Management System (WIMS)',
    description: 'Comprehensive platform for monitoring oil and gas well integrity, inspections, risk tracking, maintenance planning, and compliance reporting. Ensure regulatory compliance and prevent costly failures.',
    icon: '&#128737;',
    iconBg: 'bg-primary-500/10 text-primary-400 border border-primary-500/20',
    tags: ['Inspections', 'Risk Analysis', 'Compliance', 'Maintenance']
  },
  {
    title: 'Production & Operations Management',
    description: 'Track production data in real-time, generate forecasts, run analytics, and measure operational performance across your entire portfolio of assets.',
    icon: '&#128200;',
    iconBg: 'bg-green-500/10 text-green-400 border border-green-500/20',
    tags: ['Analytics', 'Forecasting', 'Real-time Data', 'KPIs']
  },
  {
    title: 'GIS & Geospatial Mapping',
    description: 'Visualize operational assets — wells, pipelines, facilities, and revenue locations — on interactive maps with real-time data overlays and spatial analysis tools.',
    icon: '&#127758;',
    iconBg: 'bg-accent-500/10 text-accent-400 border border-accent-500/20',
    tags: ['Interactive Maps', 'Asset Tracking', 'Spatial Analysis', 'GIS']
  }
]

const whyItems = [
  { title: 'Industry Expertise', desc: 'Deep understanding of Oil & Gas, energy, and government sector requirements.' },
  { title: 'Custom-Built Solutions', desc: 'Tailored applications designed specifically for your operational workflows.' },
  { title: 'Enterprise Security', desc: 'Built with compliance and data security at the foundation.' },
  { title: 'Scalable Architecture', desc: 'Cloud-ready platforms that grow with your organization.' }
]

const barHeights = [45, 62, 55, 78, 65, 82, 70, 88, 75, 92, 80, 95]
</script>
