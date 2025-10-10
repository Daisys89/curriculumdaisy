<template>
  <section class="space-y-8">
    <!-- Languages -->
    <div>
      <h2 class="text-3xl font-bold text-gray-900 mb-6">Talen</h2>
      <div class="bg-white rounded-2xl p-6 shadow-lg border border-gray-100">
        <div class="space-y-4">
          <div v-for="lang in languages" :key="lang.name" class="flex justify-between items-center">
            <span class="font-semibold text-gray-900">{{ lang.name }}</span>
            <span
              class="px-3 py-1 bg-gradient-to-r from-teal-100 to-cyan-100 text-teal-800 text-sm font-bold rounded-full"
            >
              {{ lang.level }}
            </span>
          </div>
        </div>
      </div>
    </div>

    <!-- Interests -->
    <div>
      <h2 class="text-3xl font-bold text-gray-900 mb-6">Interesses</h2>
      <div class="bg-white rounded-2xl p-6 shadow-lg border border-gray-100">
        <div class="flex flex-wrap gap-3">
          <span
            v-for="interest in interests"
            :key="interest"
            class="px-4 py-2 bg-gradient-to-r from-teal-500 to-cyan-500 text-white font-medium rounded-full text-sm"
          >
            {{ interest }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ExtrasSection',
  props: {
    languages: {
      type: Array,
      required: true,
    },
    interests: {
      type: Array,
      required: true,
    },
  },
}
</script>
