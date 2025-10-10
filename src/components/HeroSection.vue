<template>
  <section class="relative bg-gradient-to-r from-teal-500 to-cyan-600 pt-20 pb-6">
    <!-- Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute top-20 left-10 w-64 h-64 bg-white rounded-full blur-3xl"></div>
      <div class="absolute bottom-20 right-10 w-96 h-96 bg-white rounded-full blur-3xl"></div>
    </div>

    <div class="relative max-w-6xl mx-auto px-6 pt-20 pb-6">
      <div class="text-center mb-16">
        <!-- Profile Image -->
        <div class="relative inline-block mb-8">
          <img
            src="../assets/img/daisy.jpg"
            alt="Profielfoto"
            class="w-40 h-40 mx-auto rounded-full shadow-2xl object-cover object-top"
          />
          <div
            class="absolute -bottom-2 -right-2 w-8 h-8 bg-green-400 rounded-full border-4 border-white"
          ></div>
        </div>

        <!-- Name and Title -->
        <h1 class="text-5xl md:text-7xl font-black text-white mb-4 tracking-tight">
          <span class="block">{{ person.firstName }}</span>
          <span
            class="block bg-gradient-to-r from-teal-400 to-cyan-400 bg-clip-text text-transparent"
          >
            {{ person.lastName }}
          </span>
        </h1>

        <div class="text-2xl md:text-3xl text-teal-100 font-medium mb-6">
          {{ person.title }}
        </div>

        <p class="text-xl text-teal-100/80 max-w-3xl mx-auto mb-12 leading-relaxed">
          {{ person.tagline }}
        </p>

        <!-- Contact Links -->
        <div class="flex justify-center space-x-6">
          <a
            v-for="contact in person.contacts"
            :key="contact.type"
            :href="getContactLink(contact)"
            class="w-14 h-14 bg-white/10 backdrop-blur-sm rounded-full flex items-center justify-center text-white hover:bg-white/20 hover:scale-110 transition-all duration-300 border border-white/20"
          >
            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
              <path
                v-if="contact.type === 'email'"
                d="M3 5a2 2 0 012-2h14a2 2 0 012 2v14a2 2 0 01-2 2H5a2 2 0 01-2-2V5zM5 7v10l5.5-3 5.5 3V7H5z"
              />
              <path
                v-else-if="contact.type === 'linkedin'"
                d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
              />
              <path
                v-else-if="contact.type === 'github'"
                d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
              />
              <path
                v-else-if="contact.type === 'netlify'"
                d="M16.934 8.519a1.044 1.044 0 0 1 .303.23l2.349-1.045-2.192-2.171-.491 2.954zM12.06 6.546a1.305 1.305 0 0 1 .209.574l3.497 1.482a1.044 1.044 0 0 1 .355-.177l.574-3.55-2.13-2.234-2.505 3.852v.053zm11.933 5.491l-3.748-3.748-2.548 1.044 6.264 2.662s.053.042.032.042zm-.627.606l-6.013-2.569a1.044 1.044 0 0 1-.7.407l-.647 3.957a1.044 1.044 0 0 1 .303.731l3.633.762 3.33-3.31v-.062zM15.4 9.25L12.132 7.86a1.2 1.2 0 0 1-1.044.543h-.199L8.185 12.58l7.225-3.132v.01a.887.887 0 0 1 0-.167.052.052 0 0 0-.01-.041zm3.967 7.308l-3.195-.658a1.096 1.096 0 0 1-.46.344l-.761 4.72 4.437-4.396s-.01.02-.021.02zm-4.469-.324a1.044 1.044 0 0 1-.616-.71l-5.95-1.222-.084.136 5.398 7.81.323-.324.919-5.67s.031.022.01.011zm-6.441-2.652l5.878 1.211a1.044 1.044 0 0 1 .824-.522l.637-3.894-.135-.115-7.308 3.132a1.817 1.817 0 0 1 .104.188zm-2.464.981l-.125-.125-2.537 1.044 1.232 1.222 1.399-2.172zm1.67.397a1.368 1.368 0 0 1-.563.125 1.389 1.389 0 0 1-.45-.073l-1.544 2.245 6.765 6.702 1.19-1.18zm-.95-2.641a1.702 1.702 0 0 1 .314 0 1.378 1.378 0 0 1 .344 0l2.735-4.25a1.19 1.19 0 0 1-.334-.824 1.242 1.242 0 0 1 0-.271l-3.32-1.535-2.672 2.6zm.303-7.402l3.237 1.378a1.242 1.242 0 0 1 .835-.282 1.357 1.357 0 0 1 .397.063l2.526-3.947L11.923.041 7.016 4.854s-.01.052 0 .063zm-1.21 8.164a1.566 1.566 0 0 1 .24-.334L3.278 8.613 0 11.797l5.804 1.284zm-.262.7L.533 12.735l2.203 2.235 2.777-1.18z"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  props: {
    person: {
      type: Object,
      required: true,
    },
  },
  methods: {
    getContactLink(contact) {
      if (contact.type === 'email') {
        return `mailto:${contact.value}`
      } else if (contact.type === 'linkedin') {
        return contact.value
      } else if (contact.type === 'github') {
        return contact.value
      } else if (contact.type === 'netlify') {
        return contact.value
      }
      return '#'
    },
  },
}
</script>
