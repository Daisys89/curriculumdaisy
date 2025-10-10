<template>
  <section>
    <h2 class="text-3xl font-bold text-gray-900 mb-6">Opleiding</h2>

    <div class="space-y-6">
      <div
        v-for="edu in education"
        :key="edu.id"
        class="bg-white rounded-2xl p-6 shadow-lg border border-gray-100"
      >
        <h3 class="text-lg font-bold text-gray-900 mb-1">{{ edu.degree }}</h3>
        <p class="text-blue-600 font-semibold mb-2">{{ edu.institution }}</p>
        <p class="text-gray-600 text-sm mb-2">{{ edu.period }}</p>
        <p class="text-gray-700">{{ edu.details }}</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'EducationSection',
  props: {
    education: {
      type: Array,
      required: true,
    },
  },
}
</script>
