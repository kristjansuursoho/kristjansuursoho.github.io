<template>
  <main
    data-scroll-container
    class="flex flex-col bg-stone-100 text-stone-900"
    ref="container"
  >
    <div class="flex flex-col md:pt-6 2xl:pt-24">
      <header
        data-scroll-section
        class="flex flex-col max-w-screen-2xl w-full mx-auto px-6 md:px-12 md:gap-4"
      >
        <div
          class="flex flex-col md:flex-row md:items-end border-b-2 pb-6 border-stone-900 pt-6"
        >
          <h1 class="text-6xl md:text-8xl md:-ml-[2px] font-medium">
            Kristjan
            <br />
            Suursoho
          </h1>

          <div class="flex-1"></div>

          <div
            class="flex md:items-end flex-col max-md:pt-6 md:pb-2 text-base md:text-lg"
          >
            <a
              target="_blank"
              href="https://www.linkedin.com/in/kristjan-suursoho-a475ba166/"
              class="flex items-center gap-6 md:gap-4 group hover:text-blue-800"
            >
              <span class="material-symbols-outlined text-lg pt-[1px]">
                link
              </span>
              <span class="group-hover:underline">LinkedIn</span>
            </a>

            <a
              href="mailto:kristjan.suursoho@gmail.com"
              class="flex items-center gap-6 md:gap-4 group hover:text-blue-800"
            >
              <span class="material-symbols-outlined text-lg pt-[1px]">
                email
              </span>
              <span class="group-hover:underline">
                kristjan.suursoho@gmail.com
              </span>
            </a>
          </div>
        </div>
      </header>

      <section
        data-scroll-section
        class="max-w-screen-2xl w-full mx-auto md:gap-6 pt-6 md:pt-12 px-6 md:px-12"
      >
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-12">
          <p class="col-span-1 text-xl md:text-2xl md:leading-[1.4] questrial">
            With extensive experience collaborating with various startups and
            development agencies, I specialize in building hybrid applications,
            full-stack solutions, custom websites, and solution architecture.
          </p>

          <p class="flex-1 text-base md:text-lg">
            My approach to work is versatile and adaptable, no task is beneath
            or above me, embracing tasks of all levels of complexity with
            dedication and a willingness to learn.
            <br /><br />

            In addition to my development expertise, I have a strong interest in
            digital design, engineering, analog music production, philosophy,
            and art.
            <br /><br />

            These diverse interests enrich my professional perspective and fuel
            my creativity in problem-solving.
          </p>
        </div>
      </section>
    </div>

    <section
      data-scroll-section
      class="flex flex-col max-w-screen-2xl w-full mx-auto md:gap-6 pt-24 md:pt-24 px-6 md:px-12 md:gap-4"
    >
      <div
        v-for="skill in listOfSkills"
        class="flex flex-col gap-2 lg:gap-6 grid-cols-2"
      >
        <h5 class="text-4xl md:text-5xl leading-[1.2] mb-4">
          {{ skill.title }}
        </h5>

        <div
          class="grid grid-cols-1 md:grid-cols-2 flex-col gap-6 md:gap-12 flex-1"
        >
          <div class="grid grid-cols-1 gap-4">
            <p
              v-for="description in skill.listOfDescription"
              class="text-base md:text-lg"
            >
              {{ description }}
            </p>
          </div>

          <div class="grid grid-cols-1 gap-2">
            <template v-for="extra in skill.listOfExtra">
              <div class="flex flex-col">
                <h4 class="text-base md:text-lg">
                  {{ extra.title }}
                </h4>

                <div class="text-base flex flex-wrap">
                  <span
                    v-for="item in extra.list"
                    class="text-base mr-1 mb-1 bg-stone-800 text-white px-1"
                  >
                    {{ item }}
                  </span>
                </div>
              </div>
            </template>
          </div>
        </div>
      </div>
    </section>

    <section
      data-scroll-section
      class="flex flex-col max-w-screen-2xl w-full mx-auto md:gap-6 pt-24 md:pt-24 px-6 md:px-12 md:gap-4"
    >
      <div class="flex items-center py-6">
        <h1 class="text-3xl md:text-5xl font-bold text-amber-600">
          Work experience
        </h1>
      </div>

      <div class="flex flex-col text-stone-900">
        <div
          v-for="experience in listOfExperience"
          class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-12 py-6 border-b border-stone-900"
        >
          <div class="flex flex-col">
            <h3 class="text-xl md:text-2xl">
              <span>
                {{ experience.company }}
                <span class="opacity-60 text-base font-bold">
                  ({{ experience.from }} - {{ experience.to }})
                </span>
              </span>
            </h3>

            <span class="text-base md:text-lg">{{ experience.role }}</span>
          </div>

          <div class="flex flex-col">
            <p class="text-lg" v-html="experience.note"></p>
          </div>
        </div>
      </div>
    </section>

    <section
      data-scroll-section
      class="flex flex-col max-w-screen-2xl w-full mx-auto md:gap-6 pt-24 md:pt-24 px-6 md:px-12 md:gap-4"
    >
      <div class="flex items-center py-6">
        <h1 class="text-3xl md:text-5xl font-bold text-amber-600">
          What they say about me
        </h1>
      </div>

      <div
        class="grid md:grid-cols-1 lg:grid-cols-2 gap-12 md:gap-12 py-12 text-stone-900"
      >
        <div
          v-for="testimonial in listOfTestimonial"
          class="flex flex-col flex-1 border-l border-stone-900 pl-6"
        >
          <h3 class="text-base md:text-lg">
            <span>{{ testimonial.text }}</span>
          </h3>

          <div class="flex flex-col pt-6">
            <span class="text-base font-semibold">
              {{ testimonial.name }}
            </span>
            <span class="text-sm">
              {{ testimonial.position }}
            </span>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
import { computed, onMounted, ref, watch } from 'vue'
import LocomotiveScroll from 'locomotive-scroll'

const container = ref()

onMounted(() => {
  const scroll = new LocomotiveScroll({
    el: container.value,
    smooth: true,
  })
})

const listOfNavItem = [
  {
    label: 'Intro',
    id: 'intro',
  },
  {
    label: 'Skills',
    id: 'skills',
  },
  {
    label: 'Experience',
    id: 'experience',
  },
  {
    label: 'Testimonials',
    id: 'testimonials',
  },
  {
    label: 'Contact',
    id: 'contact',
  },
]

const listOfSkills = [
  {
    title: 'Full stack Development',
    listOfDescription: [
      'Throughout my career, I have successfully executed numerous projects, from developing web/mobile/hybrid applications, building full SSR e-commerce platforms or creating custom website solutions. I have explored and perfected various aspects of the web development, gaining extensive knowledge in web applications and API solutions.',
    ],
    listOfExtra: [
      {
        title: 'Commonly used:',
        list: [
          'TypeScript',
          'Node/Deno/Bun',
          'Express/Koa/Elysia',
          'Vue/React/Angular',
          'Capacitor',
          'Vite/Webpack',
          'Nuxt/Next',
          'SPA/WPA/SSR',
          'Python',
        ],
      },
      {
        title: 'Also interested in',
        list: ['Rust', 'Java/Kotlin', 'Go', 'Python'],
      },
    ],
  },
  {
    title: 'Solution Architecture',
    listOfDescription: [
      'As a self-motivated and detail-oriented professional, I am deeply interested in developing high-end solutions by implementing scalable, reliable, and cost-effective strategies utilizing AWS services.',
    ],
    listOfExtra: [
      {
        title: 'Commonly used:',
        list: [
          'Docker',
          'Terraform',
          'AWS IoT/Greengrass',
          'ECS',
          'VPC',
          'SQS',
          'S3',
          'DynamoDB',
          'Timestream',
        ],
      },
    ],
  },
]

const listOfExperience = [
  {
    company: 'C-BOX',
    from: '2022',
    to: '...',
    role: 'Lead developer & architect and IoT engineer',
    devTeamSize: '1',
    note: `Developed hybrid applications (Web, iOS, Android) using Vue.js with TypeScript, Docker, Node.js, and AWS services such as ECS and Amplify. Additionally, created a dynamic system for locker stations integrated with hybrid application, utilizing AWS IoT Core, Greengrass, Python, SQS, MQTT, Rust, and Node.js with TypeScript.`.trim(),
  },
  {
    company: 'Dermtest',
    from: '2022',
    to: '2024',
    role: 'Lead front-end developer',
    devTeamSize: '1-3',
    note: `Participated in developing an application for dermatologists and general doctors using Angular with TypeScript, and AWS services. Additionally, designed and created a hybrid mobile application (Web, iOS, Android) for psoriasis patients using Node.js, Capacitor, Angular with TypeScript, and AWS services.`.trim(),
  },
  {
    company: 'Flowit',
    from: '2020',
    to: '2022',
    role: 'Full Stack Developer',
    devTeamSize: '2-6',
    note: `Led front-end development for tradehouse.ee and its management system. Also contributed as a front-end developer for the Derossi Marine CMS system, utilizing Odoo, Python, Node.js, PostgreSQL, and Vue.js.`.trim(),
  },
  {
    company: 'CostPocket',
    from: '2017',
    to: '2022',
    role: 'Full Stack Developer',
    devTeamSize: '2-5',
    note: `Cornerstone of my developer journey, having designed and developed multiple web applications, a primary hybrid application, and various custom web solutions. Developed dozens of custom solutions to address diverse requirements.`.trim(),
  },
]

const listOfTestimonial = [
  {
    name: 'Eduard Kotov',
    position: 'CTO at CostPocket',
    text: 'Kristjan combines his design skills and web developer experience to bring simplicity and elegance to client experience.',
  },
  {
    name: 'Keir Volas',
    position: 'Tech Lead at Certific',
    text: 'Kristjan likes challenges and he is able to think out of the box. He is very eager to learn new things. It has been great to see his quick qrowth in front-end development in CostPocket.',
  },
  {
    name: 'Joonas Sernjuk',
    position: 'COO at CostPocket',
    text: 'It has been great to see him grow, when he started with CostPocket he only know very little about development, now he is coaching others. Kristjan is very good combination of designer and front end developer. He will first help you to design your product and then he will also build that product. Kristjan also has good work ethics, he is very positive, he is fast learner and he will never tell you that it is impossible -"if there is will there is weapon"',
  },
  {
    name: 'Viivika Lumberg',
    position: 'Key Account Manager/Email Marketing Strategist at Smaily',
    text: 'Kristjan has an extremely creative mind and all of his designs are well thought through, user friendly and beautiful. He does not just create, but he is doing a lot of research before getting to the creation part. No matter the task (website design, email template, FB ad design, video) the outcome is always stylish and user-friendly. And in addition, he has never forgotten about a task or delayed with the delivery. I am super happy to work with him!',
  },
  {
    name: 'Mirell Põllumäe',
    position: 'OKR Coach and Head of Customer Success at Wisnio',
    text: 'I have worked with Kristjan on different projects and he has done some pages for me. He is that type of person who just decides that he will achieve something and he will. His learning capability and will do develop is extremely strong. He works hard but he needs challenges to feel motivated. He suits for organisations who look for creative and ambitions people not so much to organisations who need someone to carry out repetitive tasks. It has been a pleasure!',
  },
]

const listOfContact = [
  {
    label: 'LINKEDIN',
    href: 'https://www.linkedin.com/in/kristjan-suursoho-a475ba166/',
  },
]
</script>

<style></style>
