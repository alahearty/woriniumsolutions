<template>
  <div>
    <!-- Hero -->
    <section class="relative pt-32 pb-16 md:pt-40 md:pb-24 overflow-hidden">
      <div class="absolute inset-0">
        <div class="absolute top-1/4 -left-32 w-96 h-96 bg-primary-600/15 rounded-full blur-[128px]"></div>
        <div class="absolute bottom-1/4 -right-32 w-80 h-80 bg-accent-600/10 rounded-full blur-[128px]"></div>
        <div class="absolute inset-0 bg-[linear-gradient(rgba(255,255,255,0.015)_1px,transparent_1px),linear-gradient(90deg,rgba(255,255,255,0.015)_1px,transparent_1px)] bg-[size:60px_60px]"></div>
      </div>

      <div class="container-max px-4 sm:px-6 lg:px-8 relative z-10">
        <span class="section-label">About Us</span>
        <h1 class="section-title max-w-3xl">
          Engineering <span class="gradient-text">Digital Excellence</span> for Critical Industries
        </h1>
        <p class="section-subtitle max-w-2xl mt-4">
          Worinium Solutions is an enterprise software company specializing in custom-built applications for the Oil & Gas industry, government agencies, and industrial operations.
        </p>
      </div>
    </section>

    <!-- Mission & Vision -->
    <section class="section-padding !pt-0">
      <div class="container-max">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div class="glass-card-hover p-8">
            <div class="w-12 h-12 rounded-xl bg-primary-500/10 border border-primary-500/20 flex items-center justify-center mb-6">
              <svg class="w-6 h-6 text-primary-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
              </svg>
            </div>
            <h3 class="text-xl font-display font-bold text-white mb-3">Our Mission</h3>
            <p class="text-gray-400 leading-relaxed">
              To empower organizations in the energy, government, and industrial sectors with reliable, scalable, and intelligent software solutions that drive operational efficiency and informed decision-making.
            </p>
          </div>

          <div class="glass-card-hover p-8">
            <div class="w-12 h-12 rounded-xl bg-accent-500/10 border border-accent-500/20 flex items-center justify-center mb-6">
              <svg class="w-6 h-6 text-accent-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
              </svg>
            </div>
            <h3 class="text-xl font-display font-bold text-white mb-3">Our Vision</h3>
            <p class="text-gray-400 leading-relaxed">
              To be the trusted technology partner for enterprises worldwide, delivering purpose-built software platforms that transform how critical industries manage assets, operations, and data.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- What We Do -->
    <section class="section-padding bg-dark-900/50 border-t border-white/[0.04]">
      <div class="container-max">
        <div class="text-center mb-16">
          <span class="section-label">What We Do</span>
          <h2 class="section-title">Our <span class="gradient-text">Expertise</span></h2>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div v-for="area in expertise" :key="area.title" class="glass-card-hover p-6 text-center">
            <div class="text-3xl mb-4" v-html="area.icon"></div>
            <h3 class="text-white font-semibold mb-2">{{ area.title }}</h3>
            <p class="text-sm text-gray-500 leading-relaxed">{{ area.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Values -->
    <section class="section-padding">
      <div class="container-max">
        <div class="text-center mb-16">
          <span class="section-label">Core Values</span>
          <h2 class="section-title">What <span class="gradient-text">Drives Us</span></h2>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          <div v-for="(value, i) in values" :key="value.title" class="glass-card-hover p-6">
            <span class="text-xs font-bold text-primary-500 tracking-[0.2em]">{{ String(i + 1).padStart(2, '0') }}</span>
            <h3 class="text-white font-semibold mt-3 mb-2">{{ value.title }}</h3>
            <p class="text-sm text-gray-500 leading-relaxed">{{ value.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Technology Stack -->
    <section class="section-padding bg-dark-900/50 border-t border-white/[0.04]">
      <div class="container-max">
        <div class="text-center mb-16">
          <span class="section-label">Technology</span>
          <h2 class="section-title">Our <span class="gradient-text">Tech Stack</span></h2>
          <p class="section-subtitle mx-auto">
            We leverage modern, enterprise-grade technologies to deliver reliable and scalable solutions.
          </p>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-4">
          <div
            v-for="tech in technologies"
            :key="tech"
            class="glass-card hover:bg-white/[0.06] p-4 text-center text-sm text-gray-400 font-medium transition-all duration-300 hover:text-primary-400"
          >
            {{ tech }}
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="section-padding">
      <div class="container-max text-center">
        <h2 class="section-title">Want to <span class="gradient-text">Work With Us</span>?</h2>
        <p class="section-subtitle mx-auto mt-4">
          We're always looking to partner with organizations that share our commitment to excellence.
        </p>
        <router-link to="/contact" class="btn-primary mt-8 text-base px-8 py-4">
          Get In Touch
        </router-link>
      </div>
    </section>
  </div>
</template>

<script setup>
const expertise = [
  {
    title: 'Enterprise Applications',
    icon: '&#128187;',
    desc: 'Custom web and desktop applications designed for complex business processes and large-scale operations.'
  },
  {
    title: 'Data & Analytics',
    icon: '&#128202;',
    desc: 'Business intelligence, reporting dashboards, and data management platforms for data-driven decision making.'
  },
  {
    title: 'Geospatial Solutions',
    icon: '&#127758;',
    desc: 'GIS platforms and interactive mapping applications for visualizing and managing operational assets.'
  }
]

const values = [
  {
    title: 'Reliability',
    desc: 'We build mission-critical software that organizations can depend on 24/7.'
  },
  {
    title: 'Innovation',
    desc: 'We leverage modern technologies to solve complex industry challenges.'
  },
  {
    title: 'Partnership',
    desc: 'We work alongside our clients as true technology partners, not just vendors.'
  },
  {
    title: 'Excellence',
    desc: 'We hold ourselves to the highest standards of quality in everything we deliver.'
  }
]

const technologies = [
  '.NET / C#',
  'Vue.js',
  'React',
  'Python',
  'SQL Server',
  'PostgreSQL',
  'Azure',
  'AWS',
  'ArcGIS',
  'Power BI',
  'Docker',
  'REST APIs'
]
</script>
