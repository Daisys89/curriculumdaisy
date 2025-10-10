<template>
  <section class="bg-gradient-to-r from-teal-500 to-cyan-600 py-20">
    <div class="max-w-4xl mx-auto text-center px-6">
      <h2 class="text-4xl font-bold text-white mb-6">Wil je graag meer weten?</h2>
      <div class="flex flex-col sm:flex-row gap-4 justify-center">
        <a
          href="mailto:daisy@devolvio.com"
          class="px-8 py-3 bg-white text-teal-600 font-bold rounded-full hover:bg-gray-100 transition-colors duration-200"
        >
          Neem Contact Op
        </a>
        <button
          @click="printPDF"
          class="px-8 py-3 bg-white text-teal-600 font-bold rounded-full hover:bg-gray-100 transition-colors duration-200"
        >
          Print PDF
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CTASection',
  methods: {
    printPDF() {
      window.print()
    },
  },
}
</script>
