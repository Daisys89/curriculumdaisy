<template>
  <section class="mb-20">
    <div class="text-center mb-12">
      <h2 class="text-4xl font-bold text-gray-900 mb-4">Over Mij</h2>
      <div
        class="w-24 h-1 bg-gradient-to-r from-blue-500 to-purple-500 mx-auto rounded-full"
      ></div>
    </div>

    <div class="bg-white rounded-3xl p-8 shadow-xl border border-gray-100">
      <p class="text-lg text-gray-700 leading-relaxed mb-6">{{ intro }}</p>

      <div class="grid md:grid-cols-2 gap-6">
        <div
          v-for="highlight in aboutHighlights"
          :key="highlight"
          class="flex items-start space-x-3"
        >
          <div
            class="w-6 h-6 bg-gradient-to-r from-blue-500 to-purple-500 rounded-full flex items-center justify-center flex-shrink-0 mt-0.5"
          >
            <svg class="w-3 h-3 text-white" fill="currentColor" viewBox="0 0 20 20">
              <path
                fill-rule="evenodd"
                d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                clip-rule="evenodd"
              />
            </svg>
          </div>
          <span class="text-gray-700 font-medium">{{ highlight }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutSection',
  props: {
    intro: {
      type: String,
      required: true,
    },
    aboutHighlights: {
      type: Array,
      required: true,
    },
  },
}
</script>
