<template>
  <section class="mb-20">
    <div class="text-center mb-12">
      <h2 class="text-4xl font-bold text-gray-900 mb-4">Werkervaring</h2>
      <div class="w-24 h-1 bg-gradient-to-r from-blue-500 to-purple-500 mx-auto rounded-full"></div>
    </div>

    <div class="relative">
      <!-- Timeline line -->
      <div
        class="absolute left-8 top-0 bottom-0 w-0.5 bg-gradient-to-b from-teal-500 to-cyan-500"
      ></div>

      <div class="space-y-12">
        <div v-for="job in experience" :key="job.id" class="relative pl-20">
          <!-- Timeline dot -->
          <div
            class="absolute left-6 w-4 h-4 bg-gradient-to-br from-teal-500 to-cyan-500 rounded-full border-4 border-white shadow-lg"
          ></div>

          <!-- Job card -->
          <div
            class="bg-white rounded-3xl p-8 shadow-xl border border-gray-100 hover:shadow-2xl transition-all duration-300"
          >
            <div class="flex flex-col md:flex-row md:items-start md:justify-between mb-4">
              <div class="flex-1">
                <h3 class="text-2xl font-bold text-gray-900 mb-2">{{ job.title }}</h3>
                <div class="flex items-center space-x-3 mb-2">
                  <span class="text-lg font-semibold text-teal-600">{{ job.company }}</span>
                  <span
                    class="px-3 py-1 bg-gray-100 text-gray-600 text-sm font-medium rounded-full"
                    >{{ job.type }}</span
                  >
                </div>
              </div>
              <div class="text-gray-500 font-medium">{{ job.period }}</div>
            </div>

            <p class="text-gray-700 mb-6 leading-relaxed">{{ job.description }}</p>

            <div class="flex flex-wrap gap-2">
              <span
                v-for="tech in job.technologies"
                :key="tech"
                class="px-3 py-1 bg-gradient-to-r from-blue-100 to-purple-100 text-blue-800 text-sm font-medium rounded-full"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'WorkexperienceSection',
  props: {
    experience: {
      type: Array,
      required: true,
    },
  },
}
</script>
