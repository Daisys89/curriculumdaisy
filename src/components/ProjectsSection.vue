<template>
  <section class="mb-20">
    <div class="text-center mb-12">
      <h2 class="text-4xl font-bold text-gray-900 mb-4">Portfolio Projecten</h2>
      <div class="w-24 h-1 bg-gradient-to-r from-blue-500 to-purple-500 mx-auto rounded-full"></div>
    </div>

    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div
        v-for="project in projects"
        :key="project.id"
        class="group bg-white rounded-3xl overflow-hidden shadow-xl border border-gray-100 hover:shadow-2xl hover:-translate-y-2 transition-all duration-300"
      >
        <div class="h-48 bg-gradient-to-br from-teal-500 to-cyan-600 relative overflow-hidden">
          <div
            class="absolute inset-0 bg-black/20 group-hover:bg-black/10 transition-colors duration-300"
          ></div>
          <div class="absolute inset-0 flex items-center justify-center">
            <svg class="w-16 h-16 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path
                v-if="project.title.includes('Veganfood')"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1.5"
                d="M3 3h2l.4 2M7 13h10l4-8H5.4m0 0L7 13m0 0l-2.293 2.293c-.63.63-.184 1.707.707 1.707H19M7 13v4a2 2 0 002 2h2m2 2a2 2 0 100-4 2 2 0 000 4zm6 0a2 2 0 100-4 2 2 0 000 4z"
              />
              <path
                v-else-if="project.title.includes('Music App')"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1.5"
                d="M9 18V5l12-2v13M9 18c0 1.657-1.343 3-3 3s-3-1.343-3-3 1.343-3 3-3 3 1.343 3 3zm12-2c0 1.657-1.343 3-3 3s-3-1.343-3-3 1.343-3 3-3 3 1.343 3 3z"
              />
              <g v-else>
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                  d="M12 21a9 9 0 0 0 9-9H3a9 9 0 0 0 9 9Z"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                  d="M7 21h10"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                  d="M19.5 12 22 6"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                  d="M16.25 3c.27.1.8.53.75 1.36-.06.83-.93 1.2-1 2.02-.05.78.34 1.24.73 1.62"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                  d="M11.25 3c.27.1.8.53.74 1.36-.05.83-.93 1.2-.98 2.02-.06.78.33 1.24.72 1.62"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="1.5"
                  d="M6.25 3c.27.1.8.53.75 1.36-.06.83-.93 1.2-1 2.02-.05.78.34 1.24.74 1.62"
                />
              </g>
            </svg>
          </div>
        </div>

        <div class="p-6">
          <h3 class="text-xl font-bold text-gray-900 mb-3">{{ project.title }}</h3>
          <p class="text-gray-600 mb-4 leading-relaxed">{{ project.description }}</p>

          <a
            :href="project.website"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center px-4 py-2 bg-teal-500 hover:bg-teal-600 text-white font-medium rounded-lg transition-colors duration-200"
          >
            Bekijk Project
            <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
              />
            </svg>
          </a>
          <div class="flex flex-wrap gap-2 mb-4">
            <span
              v-for="feature in project.features"
              :key="feature"
              class="px-2 py-1 bg-gray-100 text-gray-700 text-xs font-medium rounded-full"
            >
              {{ feature }}
            </span>
          </div>

          <div class="flex flex-wrap gap-2">
            <span
              v-for="tech in project.technologies"
              :key="tech"
              class="px-3 py-1 bg-gradient-to-r from-blue-100 to-purple-100 text-blue-800 text-sm font-medium rounded-full"
            >
              {{ tech }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProjectsSection',
  props: {
    projects: {
      type: Array,
      required: true,
    },
  },
}
</script>
