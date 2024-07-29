<template>
  <main
    class="prose brose-base flex flex-col text-black max-w-4xl w-full mx-auto py-8 md:py-12 lg:py-24 prose-p:mb-2 prose-p:mt-1 prose-h2:mb-2 prose-h3:mb-1 prose-h3:mt-3 prose-h4:mb-1 prose-h4:mt-0 prose-p:leading-6 prose-ul:my-0 prose-li:my-0 prose-li:marker:text-black px-6 md:px-12"
  >
    <header class="text-center">
      <div class="flex items-center flex-wrap">
        <div class="max-sm:hidden flex-1 text-left">
          <p>Tallinn, Estonia</p>
        </div>

        <div class="flex-1 text-center max-md:text-left pr-4">
          <a
            target="_blank"
            href="https://www.linkedin.com/in/kristjan-suursoho-a475ba166/"
          >
            <span class="group-hover:underline">LinkedIn</span>
          </a>
        </div>

        <div class="flex-1 text-right">
          <a href="mailto:kristjan.suursoho@gmail.com">
            <span class="group-hover:underline">
              kristjan.suursoho@gmail.com
            </span>
          </a>
        </div>
      </div>
      <div class="py-6 border-y border-black">
        <h1 class="mb-0.5">Kristjan Suursoho</h1>
      </div>
      <div class="text-center md:px-6 pt-2">
        <p>
          For the last decade or so I've been heavily involved with building
          start-ups or working with development agencies. During this time I've
          been lucky to acquire a handful of skills while creating scalable and
          reliable solutions for the web and mobile. On my off days I'm drawn to
          analog music, engineering, philosophy, and art. I hope to encounter a
          position which allows me to build upon the abilities so far acquired.
        </p>
      </div>
    </header>

    <section class="divide-y divide-black">
      <h2>Skills and ambitions</h2>
      <div class="flex flex-col gap-2 pt-2">
        <div v-for="skill in listOfSkills">
          <h3>{{ skill.title }}</h3>
          <p>{{ skill.description }}</p>

          <div v-for="extra in skill.listOfExtra" class="pt-1 flex flex-wrap">
            <p class="mr-2 !mb-0 !mt-0">{{ extra.title }}</p>
            <p
              class="mr-2 !mb-0 !mt-0 italic"
              v-for="(item, index) in extra.list"
            >
              <span
                >{{ item }}{{ index < extra.list.length - 1 ? ',' : '.' }}</span
              >
            </p>
          </div>
        </div>
      </div>
    </section>

    <section class="divide-y divide-black">
      <h2>Professional Experience</h2>
      <div class="flex flex-col gap-2 pt-2">
        <div v-for="experience in listOfExperience">
          <h3>{{ experience.company }}</h3>
          <div class="flex items-end">
            <h4>{{ experience.role }}</h4>
            <div class="flex-1 w-12"></div>
            <h4 class="text-right">
              {{ experience.from }} - {{ experience.to }}
            </h4>
          </div>
          <ul>
            <li v-for="note in experience.listOfNote">{{ note }}</li>
          </ul>
        </div>
      </div>
    </section>

    <section class="divide-y divide-black">
      <h2>Testimonials</h2>
      <div class="flex flex-col gap-2 pt-2">
        <div v-for="testimonial in listOfTestimonial">
          <div class="flex max-sm:flex-col sm:items-end">
            <h3>{{ testimonial.name }}</h3>
            <div class="flex-1"></div>
            <h4 class="sm:text-right">{{ testimonial.position }}</h4>
          </div>
          <p v-html="testimonial.text"></p>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
const listOfSkills = [
  {
    title: 'Full stack Development',
    description:
      'The majority of my working hours have been dedicated to designing, developing, and managing different web and mobile solutions. I am eager to build and perfect various aspects of web applications, managmenent tools, micorservices or custom solutions.',
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
        title: 'Also interested in: ',
        list: ['Rust', 'Java/Kotlin', 'Go'],
      },
    ],
  },
  {
    title: 'Solution Architecture',
    description:
      'As a dedicated and detail-oriented professional, I am passionate about developing robust and cost-effective strategies using AWS services.',
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
    to: 'Present',
    role: 'Lead developer & IoT engineer',
    devTeamSize: '1',
    listOfNote: [
      'Designed and developed end-to-end system for urban smart locker stations, ensuring reliable integration with various web and mobile solutions, utilizing AWS IoT Core, Greengrass, Python, SQS, MQTT, Rust, and Node.js with TypeScript.',
      'Developed hybrid application (iOS, Android, WEB) using Vue.js with TypeScript, Docker, Node.js, and AWS services such as ECS and Amplify',
    ],
  },
  {
    company: 'Dermtest',
    from: '2022',
    to: '2024',
    role: 'Lead front-end developer',
    devTeamSize: '1-3',
    listOfNote: [
      'Participated in developing an application for dermatologists and general doctors using Angular with TypeScript, and AWS services.',
      'Designed and developed a hybrid mobile application for psoriasis patients using Node.js, Capacitor, Angular with TypeScript, and AWS services.',
    ],
  },
  {
    company: 'Flowit',
    from: '2020',
    to: '2022',
    role: 'Full Stack Developer',
    devTeamSize: '2-6',
    listOfNote: [
      'Led front-end development for tradehouse.ee and its management system.',
      'Contributed as a front-end developer for the Derossi Marine CMS system, utilizing Odoo, Python, Node.js, PostgreSQL, and Vue.js.',
    ],
  },
  {
    company: 'CostPocket',
    from: '2017',
    to: '2022',
    role: 'Full Stack Developer',
    devTeamSize: '2-5',
    listOfNote: [
      'Developed multiple web applications, a primary hybrid application, and various custom web solutions.',
      'Designed and developed an application for digitizing receipts and cost documents, processing over 30 000 documents per month.',
    ],
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
</script>
