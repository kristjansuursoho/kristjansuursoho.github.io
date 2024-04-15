<template>
  <main class="flex flex-col bg-stone-50">
    <header
      class="z-[1] flex uppercase text-lg space-x-4 pb-4 font-medium p-12"
    >
      <span>
        <a class="bg-stone-50 hover:bg-stone-900 hover:text-stone-50" href="">
          Kristjan Suursoho - CV
        </a>
      </span>
      <div class="flex-1"></div>

      <div class="flex flex-col text-right">
        <span v-for="navItem in listOfNavItem">
          <a
            class="bg-stone-50 hover:bg-stone-900 hover:text-stone-50"
            :href="`#${navItem.id}`"
          >
            {{ navItem.label }}
          </a>
        </span>
      </div>
    </header>

    <section id="intro" class="flex items-center justify-center">
      <div class="py-12 md:py-32 smax-w-6xl mx-auto px-12">
        <h1
          class="text-xl md:text-5xl leading-[1.2] upperase font-semibold text-stone-900 uppercase"
        >
          <span class="w-24 h-4 inline-block"></span>
          With competence in
          <span class="text-blue-600">full-stack development</span>,
          <span class="text-blue-600">solution architecture</span>, and
          <span class="text-blue-600">design</span>, I ensure that digital
          presence is not only flawlessly functional but also visually
          practical.
          <br />
          <span class="w-24 h-4 inline-block"></span>
          I'm driven by a passion for innovation and my ability to balance
          aesthetics with functionality.
        </h1>
      </div>
    </section>

    <section id="skills" class="p-12">
      <div class="flex flex-wrap text-stone-900">
        <div v-for="skill in listOfSkills" class="flex flex-col py-6">
          <h3
            class="text-2xl md:text-5xl leading-[1.2] upperase font-semibold uppercase mb-4"
          >
            {{ skill.title }}
          </h3>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <p
              v-for="description in skill.listOfDescription"
              class="text-lg upperase font-medium uppercase"
            >
              {{ description }}
            </p>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <template v-for="extra in skill.listOfExtra">
              <div class="flex flex-col pt-4">
                <h5 class="text-base font-regular uppercase">
                  {{ extra.title }}
                </h5>
                <div class="text-base flex flex-wrap">
                  <span
                    v-for="item in extra.list"
                    class="mr-1 mb-1 bg-stone-900 text-stone-50 px-1"
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

    <section id="experience" class="p-12">
      <div class="flex items-end border-b-2 border-stone-900 py-6">
        <h1 class="text-2xl md:text-5xl font-bold">NOTABLE EXPERIENCE</h1>
      </div>

      <div class="flex flex-col text-stone-900">
        <div
          v-for="experience in listOfExperience"
          class="grid grid-cols-1 lg:grid-cols-4 gap-4 lg:gap-12 py-6 text-lg font-medium uppercase"
        >
          <div class="row-start-1 col-span-1 flex items-start text-lg">
            <span>{{ experience.from }}</span>
            <span>-</span>
            <span>{{ experience.to }}</span>
          </div>

          <div class="row-start-2 lg:row-start-1 col-span-1">
            <h3 class="font-bold">
              <span>{{ experience.role }}</span> <br />
              <span class="font-thin"> {{ experience.company }} </span>
            </h3>
          </div>

          <div class="col-span-2">
            <p
              class="text-sm font-medium !leading-[1.8]"
              v-html="experience.note"
            ></p>

            <p class="text-sm font-medium">
              Dev team size: {{ experience.devTeamSize }}
            </p>
          </div>
        </div>
      </div>
    </section>

    <section id="testimonials" class="p-12">
      <div class="flex items-center border-b-2 border-stone-900 py-6">
        <h1 class="text-2xl md:text-5xl font-bold">WHAT THEY SAY ABOUT ME</h1>
      </div>

      <div
        class="grid md:grid-cols-3 lg:grid-cols-4 gap-12 py-12 text-stone-900"
      >
        <div
          v-for="testimonial in listOfTestimonial"
          class="flex flex-col flex-1"
        >
          <h3 class="text-sm !leading-[1.8] font-medium uppercase">
            <span>{{ testimonial.text }}</span>
          </h3>

          <div class="flex items-start space-x-6 pt-6">
            <span
              class="text-sm font-semibold uppercase"
              v-html="testimonial.name"
            >
            </span>
            <span class="flex-1"></span>
            <span class="text-sm font-regular uppercase text-right">
              {{ testimonial.position }}
            </span>
          </div>
        </div>
      </div>
    </section>

    <section id="contact" class="p-12 min-h-screen">
      <div class="flex items-center border-b-2 border-stone-900 py-6">
        <h1 class="text-2xl md:text-5xl font-bold">CONTACT</h1>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-4 gap-6 text-stone-900 py-4">
        <div v-for="item in listOfContact">
          <a :href="item.href" target="_blank" class="text-3xl font-semibold">
            {{ item.label }}
          </a>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
import { computed, onMounted, ref, watch } from 'vue'

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
      'My proficiency in various programming languages and frameworks, combined with my comprehensive understanding of software development methodologies, allows me to approach projects from an analytical and strategic perspective.',
    ],
    listOfExtra: [
      {
        title: 'COMMONLY USED:',
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
        title: 'INTERESTED IN FUTHER EXPAND MY KNOWLEDGE IN::',
        list: ['Rust', 'Java/Kotlin'],
      },
    ],
  },
  {
    title: 'Solution Architecture',
    listOfDescription: [
      'As a self-motivated and detail-oriented professional, I am deeply interested in developing high-end solutions by implementing scalable, reliable, and cost-effective strategies utilizing AWS services.',
      'From end-to-end IoT solutions to fully scalable cloud architectures, I have considerable experience designing and implementing service-oriented applications.',
    ],
    listOfExtra: [
      {
        title: 'COMMONLY USED:',
        list: [
          'Docker',
          'Terraform',
          'AWS IoT/Greengrass',
          'ECS',
          'VPC',
          'SQS',
          'S3/DynamoDB/Timestream',
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
    note: `
      # Hybrid Application (Web, IOS, Android) with vue + ts, docker, nodejs, aws ECS, Amplify. <br>
      # Dynamic System for locker stations that is integrated with application. (AWS IOT Core, greengrass, python, SQS, MQTT, rust, nodejs + ts).
    `.trim(),
  },
  {
    company: 'Dermtest',
    from: '2022',
    to: '2024',
    role: 'Lead front-end developer',
    devTeamSize: '1-3',
    note: `
      # Application for dermatologist, doctors and general doctors (Docker, angular + ts, AWS amplify). <br>
      # Hybrid Mobile application (Web, IOS, Android) for psoriasis patients (NodeJs, Capacitor, angular + ts, amplify).
    `.trim(),
  },
  {
    company: 'Flowit',
    from: '2020',
    to: '2022',
    role: 'Full Stack Developer',
    devTeamSize: '1-6',
    note: `
      # Lead front-end for tradehouse.ee + management system. <br>
      # Front-end developer for Derossi marine CMS system (Odoo, Python, NodeJs, Postgres, Vue).
    `.trim(),
  },
  {
    company: 'CostPocket',
    from: '2018',
    to: '2022',
    role: 'Full Stack Developer',
    devTeamSize: '2-5',
    note: `
      # Multiple Web applications and a main hybrid application. Different custom solutions for the web. <br>
    `.trim(),
  },
]

const listOfTestimonial = [
  {
    name: 'Eduard <br> Kotov',
    position: 'CTO at CostPocket',
    text: 'Kristjan combines his design skills and web developer experience to bring simplicity and elegance to client experience.',
  },
  {
    name: 'Keir <br> Volas',
    position: 'Tech Lead at Certific',
    text: 'Kristjan likes challenges and he is able to think out of the box. He is very eager to learn new things. It has been great to see his quick qrowth in front-end development in CostPocket.',
  },
  {
    name: 'Joonas <br> Sernjuk',
    position: 'COO at CostPocket',
    text: 'It has been great to see him grow, when he started with CostPocket he only know very little about development, now he is coaching others. Kristjan is very good combination of designer and front end developer. He will first help you to design your product and then he will also build that product. Kristjan also has good work ethics, he is very positive, he is fast learner and he will never tell you that it is impossible -"if there is will there is weapon"',
  },

  // {
  //   name: 'Viivika <br> Lumberg',
  //   position: 'Key Account Manager/Email Marketing Strategist at Smaily',
  //   text: 'Kristjan has an extremely creative mind and all of his designs are well thought through, user friendly and beautiful. He does not just create, but he is doing a lot of research before getting to the creation part. No matter the task (website design, email template, FB ad design, video) the outcome is always stylish and user-friendly. And in addition, he has never forgotten about a task or delayed with the delivery. I am super happy to work with him!',
  // },
  {
    name: 'Mirell <br> Põllumäe',
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
