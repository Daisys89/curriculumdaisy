<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Hero Section -->
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

    <div class="max-w-6xl mx-auto px-6 py-16">
      <!-- About Section -->
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

      <!-- Skills Section -->
      <section class="mb-20">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Technische Vaardigheden</h2>
          <div
            class="w-24 h-1 bg-gradient-to-r from-blue-500 to-purple-500 mx-auto rounded-full"
          ></div>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div
            v-for="category in skillCategories"
            :key="category.name"
            class="bg-white rounded-3xl p-8 shadow-xl border border-gray-100 hover:shadow-2xl transition-all duration-300"
          >
            <div class="text-center mb-6">
              <div
                class="w-16 h-16 bg-gradient-to-br from-teal-500 to-cyan-500 rounded-2xl flex items-center justify-center mx-auto mb-4"
              >
                <svg
                  class="w-8 h-8 text-white"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    v-if="category.name === 'Frontend'"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zM21 5a2 2 0 00-2-2h-4a2 2 0 00-2 2v6a2 2 0 002 2h4a2 2 0 002-2V5z"
                  />
                  <path
                    v-else-if="category.name === 'Backend'"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"
                  />
                  <path
                    v-else
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4"
                  />
                </svg>
              </div>
              <h3 class="text-xl font-bold text-gray-900">{{ category.name }}</h3>
            </div>

            <div class="space-y-4">
              <div v-for="skill in category.skills" :key="skill.name" class="skill-item">
                <div class="flex justify-between items-center mb-2">
                  <span
                    class="px-4 py-2 bg-gradient-to-r from-teal-500 to-cyan-500 text-white font-medium rounded-full text-sm"
                    >{{ skill.name }}</span
                  >
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Experience Timeline -->
      <section class="mb-20">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Werkervaring</h2>
          <div
            class="w-24 h-1 bg-gradient-to-r from-blue-500 to-purple-500 mx-auto rounded-full"
          ></div>
        </div>

        <div class="relative">
          <!-- Timeline line -->
          <div
            class="absolute left-8 top-0 bottom-0 w-0.5 bg-gradient-to-b from-teal-500 to-cyan-500"
          ></div>

          <div class="space-y-12">
            <div v-for="(job, index) in experience" :key="job.id" class="relative pl-20">
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

      <!-- Projects Section -->
      <section class="mb-20">
        <div class="text-center mb-12">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Featured Projects</h2>
          <div
            class="w-24 h-1 bg-gradient-to-r from-blue-500 to-purple-500 mx-auto rounded-full"
          ></div>
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
                <svg
                  class="w-16 h-16 text-white"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    v-if="project.title.includes('Healthcare')"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="1.5"
                    d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"
                  />
                  <path
                    v-else-if="project.title.includes('E-commerce')"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="1.5"
                    d="M3 3h2l.4 2M7 13h10l4-8H5.4m0 0L7 13m0 0l-2.293 2.293c-.63.63-.184 1.707.707 1.707H19M7 13v4a2 2 0 002 2h2m2 2a2 2 0 100-4 2 2 0 000 4zm6 0a2 2 0 100-4 2 2 0 000 4z"
                  />
                  <path
                    v-else
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="1.5"
                    d="M9 5H7a2 2 0 00-2 2v10a2 2 0 002 2h8a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2m-3 7h3m-3 4h3m-6-4h.01M9 16h.01"
                  />
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

      <!-- Education & Footer -->
      <div class="grid md:grid-cols-2 gap-12">
        <!-- Education -->
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

        <!-- Languages & Interests -->
        <section class="space-y-8">
          <!-- Languages -->
          <div>
            <h2 class="text-3xl font-bold text-gray-900 mb-6">Talen</h2>
            <div class="bg-white rounded-2xl p-6 shadow-lg border border-gray-100">
              <div class="space-y-4">
                <div
                  v-for="lang in languages"
                  :key="lang.name"
                  class="flex justify-between items-center"
                >
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
      </div>
    </div>

    <!-- CTA Section -->
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
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'PremiumCV',
  data() {
    return {
      person: {
        name: 'Daisy Simons',
        firstName: 'Daisy',
        lastName: 'Simons',
        title: 'Full Stack Developer',
        tagline: 'Om het plaatje compleet te maken',
        contacts: [
          { type: 'email', value: 'daisy@devolvio.com' },
          { type: 'linkedin', value: 'https://linkedin.com/in/daisysimons' },
          { type: 'github', value: 'https://github.com/daisys89' },
          { type: 'netlify', value: 'https://app.netlify.com/teams/daisys89/projects' },
        ],
      },
      intro:
        'Een geboren computer liefhebber, ik ben het kind van een programmeur dus het is er met de paplepel ingegoten. Via een kleine omweg door de dierenwereld ben ik in 2021 eindelijk gaan programmeren. Ik ben begonnen met een full stack training, echter lag mijn voorkeur al heel snel bij de Front-end. Ik heb ondertussen ervaring met meerdere talen en de afgelopen tijd vooral bezig geweest met Vue.js, Tailwind en Firebase. Ik vind het heerlijk om direct resultaat te zien van mijn werk en niets leukers dan lang stoeien en proberen tot het naar mijn zin is.',
      aboutHighlights: [
        'Bekend met Vue.js maar ook React en SolidJS',
        'Ervaren met HTML, CSS, Bootstrap en Tailwind',
        'Flexibele werkstijl, gewend aan Agile, Scrum, Kanban en waterval',
        'Leergierig en pakt snel dingen op',
      ],
      skillCategories: [
        {
          name: 'Frontend',
          skills: [
            { name: 'Vue.js' },
            { name: 'React' },
            { name: 'SolidJS' },
            { name: 'Tailwind CSS' },
            { name: 'Bootstrap' },
            { name: 'HTML + CSS' },
          ],
        },
        {
          name: 'Backend',
          skills: [{ name: 'Progress ABL' }, { name: 'Node.js' }],
        },
        {
          name: 'Database & Tools',
          skills: [
            { name: 'Firebase' },
            { name: 'REST API' },
            { name: 'ChatGpt' },
            { name: 'Claud.ai' },
            { name: 'UX Pilot' },
          ],
        },
      ],
      experience: [
        {
          id: 1,
          title: 'Full Stack Developer',
          company: 'Devolvio',
          type: 'Fulltime',
          period: '2022 - Heden',
          description:
            'Het eerste jaar een allround Full Stack Development training gehad, in maart 2023 begonnen bij het Ministerie van Justitie als Progress ABL ontwikkelaar. Bij JIO gewerkt met waterval, Agile en Kanban. Hier veel meegekregen over werken in grote teams waar veel besproken en overlegd moet worden. Vorig jaar met een POC de oude applicatie van een nieuwe Front-end voorzien, zonder hulp van AI. Dat project afgelopen maand weer opgepakt en nu met behulp van UX Pilot, Vue, Tailwind en Claude een nog mooiere Front-end aan het maken.',

          technologies: ['Vue.js', 'UX pilot', 'Tailwind', 'Claude.ai', 'Progress ABL'],
        },
        {
          id: 2,
          title: 'Customer Support Consultant Level III',
          company: 'IDEXX Laboratories',
          type: 'Parttime',
          period: '2011 - 2022',
          description:
            'Klanten telefonisch en per mail te woord staan. Daarnaast verantwoordelijk om al het trainingsmateriaal op één plek beschikbaar te maken voor het team. Verzamelen van alle informatie van de verschillende servers en folders, controleren of informatie nog correct is en het op de interne website plaatsen. Ervoor zorgen dat team op de hoogte is van nieuw en/of gewijzigd materiaal. Team coachen op gesprekken en case management, 2 à 3 gesprekken afluisteren en case in systeem controleren, feedback in persoon bespreken.',

          technologies: ['Salesforce', 'Animana', 'Training', 'Documentatie'],
        },
      ],
      projects: [
        {
          id: 1,
          title: 'Veganfood',
          description: 'Een simpele overzichtelijk website om gezonde maaltijdboxen te bestellen .',
          technologies: ['HTML', 'CSS', 'Responsive', 'Webdesign'],
          website: 'https://delightful-veganfood.netlify.app/',
        },
        {
          id: 2,
          title: 'Music App',
          description: 'Een web-app om muziek te uploaden, downloaden en af te spelen.',
          technologies: ['Vue', 'Vue Router', 'TailwindCSS', 'API', 'Firebase'],
          website: 'https://daisysmusicapp.netlify.app/',
        },
        {
          id: 3,
          title: 'Bowls',
          description: 'In React een app ontworpen en ontwikkeld om eten te bestellen.',
          technologies: ['React ', 'Webdesign', 'Css'],
          website: 'https://food-bowl-app.netlify.app/',
        },
      ],
      education: [
        {
          id: 1,
          degree: 'Bachelor Diermanagement (HBO)',
          institution: 'Van Hall Larenstein',
          period: '2006 - 2010',
          details: 'Major: Paard & Management | Minor: Beleid & Communicatie',
        },
        {
          id: 2,
          degree: 'Havo',
          institution: 'Gemeentelijke Scholengemeenschap',
          period: '2001 - 2006',
          details: 'Profiel: Natuur & Gezondheid en Economie',
        },
      ],
      languages: [
        { name: 'Nederlands', level: 'Moedertaal' },
        { name: 'Engels', level: 'C2' },
        { name: 'Spaans', level: 'A1' },
      ],
      interests: ['Paarden', 'Fotografie', 'Films', 'Tuinieren', 'Vintage'],
    }
  },
  mounted() {
    this.animateSkillBars()
  },
  methods: {
    getInitials(name) {
      return name
        .split(' ')
        .map((n) => n[0])
        .join('')
    },
    getContactLink(contact) {
      if (contact.type === 'email') {
        return `mailto:${contact.value}`
      }
      return contact.value
    },
    animateSkillBars() {
      setTimeout(() => {
        const skillBars = document.querySelectorAll('.skill-bar')
        skillBars.forEach((bar) => {
          const width = bar.getAttribute('data-width')
          bar.style.width = width
        })
      }, 500)
    },
  },
}
</script>
