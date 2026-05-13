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
        <span class="section-label">Our Solutions</span>
        <h1 class="section-title max-w-3xl">
          Enterprise Software <span class="gradient-text">Built for Industry</span>
        </h1>
        <p class="section-subtitle max-w-2xl mt-4">
          From well integrity management to geospatial visualization, our platforms are purpose-built for the unique challenges of energy, government, and industrial operations.
        </p>
      </div>
    </section>

    <!-- Solutions Grid -->
    <section class="section-padding !pt-0">
      <div class="container-max">
        <div class="space-y-8">
          <div
            v-for="(solution, i) in solutions"
            :key="solution.title"
            class="glass-card-hover overflow-hidden"
          >
            <div class="p-6 md:p-10">
              <div class="flex flex-col lg:flex-row gap-8">
                <!-- Info -->
                <div class="flex-1">
                  <div class="flex items-center gap-3 mb-4">
                    <div class="w-11 h-11 rounded-xl flex items-center justify-center text-lg" :class="solution.iconBg">
                      <span v-html="solution.icon"></span>
                    </div>
                    <div>
                      <span class="text-[10px] font-bold tracking-[0.2em] uppercase text-primary-500">{{ String(i + 1).padStart(2, '0') }}</span>
                      <h2 class="text-xl font-display font-bold text-white">{{ solution.title }}</h2>
                    </div>
                  </div>
                  <p class="text-gray-400 leading-relaxed mb-6">{{ solution.description }}</p>

                  <h4 class="text-xs font-semibold text-gray-500 uppercase tracking-wider mb-3">Key Capabilities</h4>
                  <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
                    <div
                      v-for="feature in solution.features"
                      :key="feature"
                      class="flex items-center gap-2 text-sm text-gray-400"
                    >
                      <svg class="w-4 h-4 text-primary-500 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                      </svg>
                      {{ feature }}
                    </div>
                  </div>
                </div>

                <!-- Tags sidebar -->
                <div class="lg:w-64 shrink-0">
                  <div class="glass-card p-5 rounded-xl">
                    <h4 class="text-xs font-semibold text-gray-500 uppercase tracking-wider mb-3">Technologies</h4>
                    <div class="flex flex-wrap gap-2">
                      <span
                        v-for="tag in solution.tags"
                        :key="tag"
                        class="px-3 py-1 text-xs rounded-full bg-white/[0.04] text-gray-400 border border-white/[0.06]"
                      >
                        {{ tag }}
                      </span>
                    </div>

                    <h4 class="text-xs font-semibold text-gray-500 uppercase tracking-wider mt-5 mb-3">For</h4>
                    <div class="flex flex-wrap gap-2">
                      <span
                        v-for="audience in solution.audience"
                        :key="audience"
                        class="px-3 py-1 text-xs rounded-full bg-primary-500/10 text-primary-400 border border-primary-500/20"
                      >
                        {{ audience }}
                      </span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Services -->
    <section class="section-padding bg-dark-900/50 border-t border-white/[0.04]">
      <div class="container-max">
        <div class="text-center mb-16">
          <span class="section-label">Services</span>
          <h2 class="section-title">How We <span class="gradient-text">Deliver</span></h2>
          <p class="section-subtitle mx-auto">
            From licensing to custom development, we offer flexible engagement models.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="service in services" :key="service.title" class="glass-card-hover p-6">
            <div class="w-10 h-10 rounded-lg bg-primary-500/10 border border-primary-500/20 flex items-center justify-center mb-4">
              <span class="text-lg" v-html="service.icon"></span>
            </div>
            <h3 class="text-white font-semibold mb-2">{{ service.title }}</h3>
            <p class="text-sm text-gray-500 leading-relaxed">{{ service.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="section-padding">
      <div class="container-max text-center">
        <h2 class="section-title">Need a <span class="gradient-text">Custom Solution</span>?</h2>
        <p class="section-subtitle mx-auto mt-4">
          Our team specializes in building tailored enterprise software. Let's discuss your requirements.
        </p>
        <router-link to="/contact" class="btn-primary mt-8 text-base px-8 py-4">
          Start a Conversation
        </router-link>
      </div>
    </section>
  </div>
</template>

<script setup>
const solutions = [
  {
    title: 'Well Integrity Management System (WIMS)',
    description: 'A comprehensive platform for monitoring oil and gas well integrity throughout the entire lifecycle. Track inspections, manage risk assessments, plan maintenance activities, and ensure full regulatory compliance with automated reporting.',
    icon: '&#128737;',
    iconBg: 'bg-primary-500/10 text-primary-400 border border-primary-500/20',
    features: [
      'Well status monitoring',
      'Inspection management',
      'Risk assessment & tracking',
      'Maintenance planning',
      'Compliance reporting',
      'Anomaly detection',
      'Historical data analysis',
      'Regulatory dashboards'
    ],
    tags: ['Web App', 'Desktop', 'SQL Server', 'REST API', '.NET'],
    audience: ['Oil & Gas', 'Energy']
  },
  {
    title: 'Production & Operations Management',
    description: 'End-to-end production data management platform for tracking operational output, running forecasts, performing analytics, and measuring performance across your asset portfolio. Make data-driven decisions with real-time insights.',
    icon: '&#128200;',
    iconBg: 'bg-green-500/10 text-green-400 border border-green-500/20',
    features: [
      'Production data tracking',
      'Performance forecasting',
      'Operational analytics',
      'KPI dashboards',
      'Allocation reporting',
      'Decline curve analysis',
      'Multi-asset portfolio view',
      'Export & integration APIs'
    ],
    tags: ['Cloud', 'Analytics', 'Power BI', 'Python', 'SQL'],
    audience: ['Oil & Gas', 'Energy', 'Industrial']
  },
  {
    title: 'GIS & Geospatial Mapping Platform',
    description: 'Visualize operational assets including wells, pipelines, facilities, and revenue locations on interactive maps. Overlay real-time operational data with spatial analysis tools for informed decision-making.',
    icon: '&#127758;',
    iconBg: 'bg-accent-500/10 text-accent-400 border border-accent-500/20',
    features: [
      'Interactive mapping',
      'Asset geolocation',
      'Pipeline visualization',
      'Facility management',
      'Revenue location tracking',
      'Real-time data overlays',
      'Spatial analysis tools',
      'Custom layer management'
    ],
    tags: ['ArcGIS', 'Leaflet', 'PostGIS', 'Web GIS', 'API'],
    audience: ['Oil & Gas', 'Government', 'Utilities']
  },
  {
    title: 'Enterprise Workflow & Reporting',
    description: 'Streamline internal processes with automated workflow engines, approval chains, and comprehensive reporting systems. Reduce manual effort and improve data accuracy across your organization.',
    icon: '&#9881;',
    iconBg: 'bg-yellow-500/10 text-yellow-400 border border-yellow-500/20',
    features: [
      'Process automation',
      'Approval workflows',
      'Document management',
      'Custom report builder',
      'Data validation',
      'Audit trails',
      'Role-based access',
      'Email notifications'
    ],
    tags: ['.NET', 'Vue.js', 'SQL Server', 'Azure', 'REST'],
    audience: ['Government', 'Enterprise', 'Industrial']
  },
  {
    title: 'Custom Software Development',
    description: 'Tailored web, desktop, cloud, and database-driven applications built to your exact specifications. Our team works closely with you from requirements through deployment and ongoing support.',
    icon: '&#128187;',
    iconBg: 'bg-purple-500/10 text-purple-400 border border-purple-500/20',
    features: [
      'Web applications',
      'Desktop applications',
      'Cloud-native solutions',
      'Database design',
      'API development',
      'System integration',
      'Migration services',
      'Ongoing maintenance'
    ],
    tags: ['Vue.js', 'React', '.NET', 'Python', 'Azure', 'AWS'],
    audience: ['All Industries']
  }
]

const services = [
  {
    title: 'Software Licensing',
    icon: '&#128273;',
    desc: 'Flexible licensing models for our enterprise products including perpetual and subscription options.'
  },
  {
    title: 'SaaS Platform Access',
    icon: '&#9729;',
    desc: 'Cloud-hosted solutions with managed infrastructure, updates, and 24/7 monitoring.'
  },
  {
    title: 'Enterprise Deployment',
    icon: '&#127959;',
    desc: 'On-premise or private cloud deployment with full customization and integration support.'
  },
  {
    title: 'Maintenance & Support',
    icon: '&#128736;',
    desc: 'Ongoing maintenance contracts with SLA-backed support, updates, and performance optimization.'
  },
  {
    title: 'Custom Development',
    icon: '&#128296;',
    desc: 'Bespoke software development services tailored to your specific business requirements.'
  },
  {
    title: 'Consulting & Technical Support',
    icon: '&#128101;',
    desc: 'Expert consulting for technology strategy, architecture planning, and system optimization.'
  }
]
</script>
