<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Hero Section -->
    <HeroSection :person="person" />
    <div class="max-w-6xl mx-auto px-6 py-16">
      <!-- About Section -->
      <AboutSection :intro="intro" :about-highlights="aboutHighlights" />

      <!-- Skills Section -->
      <SkillsSection :skill-categories="skillCategories" />

      <!-- Workexperience Section -->
      <WorkexperienceSection :experience="experience" />

      <!-- Projects Section -->
      <ProjectsSection :projects="projects" />

      <!-- Education & Extras -->
      <div class="grid md:grid-cols-2 gap-12">
        <!-- Education -->
        <EducationSection :education="education" />

        <!-- Extra's: Languages & Interests -->
        <ExtrasSection :languages="languages" :interests="interests" />
      </div>
    </div>

    <!-- Call to Action Section -->
    <CTASection />
  </div>
</template>

<script>
import HeroSection from '@/components/HeroSection.vue'
import AboutSection from '@/components/AboutSection.vue'
import SkillsSection from '@/components/SkillsSection.vue'
import WorkexperienceSection from '@/components/WorkexperienceSection.vue'
import ProjectsSection from '@/components/ProjectsSection.vue'
import EducationSection from '@/components/EducationSection.vue'
import ExtrasSection from '@/components/ExtrasSection.vue'
import CTASection from '@/components/CTASection.vue'

export default {
  name: 'PremiumCV',
  components: {
    AboutSection,
    HeroSection,
    SkillsSection,
    WorkexperienceSection,
    ProjectsSection,
    EducationSection,
    ExtrasSection,
    CTASection,
  },
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
            { name: 'JIRA' },
            { name: 'Confluence' },
            { name: 'Bitbucket' },
            { name: 'Gitlab' },
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
          period: '2019 - 2022',
          description:
            'Klanten telefonisch en per mail te woord staan. Daarnaast verantwoordelijk om al het trainingsmateriaal op één plek beschikbaar te maken voor het team. Verzamelen van alle informatie van de verschillende servers en folders, controleren of informatie nog correct is en het op de interne website plaatsen. Ervoor zorgen dat team op de hoogte is van nieuw en/of gewijzigd materiaal. Team coachen op gesprekken en case management, 2 à 3 gesprekken afluisteren en case in systeem controleren, feedback in persoon bespreken.',

          technologies: ['Salesforce', 'Animana', 'Training', 'Documentatie'],
        },
        {
          id: 3,
          title: 'Customer Support Supervisor',
          company: 'IDEXX Laboratories',
          type: 'Parttime',
          period: '2016 - 2019',
          description:
            "Verantwoordelijk voor het Nederlandse, Belgische en Scandinavische team, totaal 7 personen. Waarborgen van dagelijkse routine, opvolgen van BPI's, planning bijhouden, superuser voor implementatie SalesForce ServiceCloud. Daarnaast regelmatig meedraaien met het team om vroegtijdig eventuele problemen te onderscheppen en deze snel te kunnen tackelen.",
          technologies: ['Salesforce', 'Animana'],
        },
        {
          id: 4,
          title: 'Customer Support Consultant Level I',
          company: 'IDEXX Laboratories',
          type: 'Parttime',
          period: '2011 - 2016',
          description:
            'Verantwoordelijk voor het beantwoorden van telefoon, voicemail, email en fax. Klanten helpen met onder andere vragen over speciale test protocollen, benodigde materialen, prijzen, uitslagen of koerierdienst.',

          technologies: ['C/lab', 'Putty', 'Einsender', 'Outlook', 'Avaya'],
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
        {
          id: 3,
          degree: 'Sportmasseur Paard',
          institution: 'Aeres Training Centre',
          period: '2017 - 2018',
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
