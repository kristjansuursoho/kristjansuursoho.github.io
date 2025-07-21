<template>
  <div class="md:p-12">
    <main
      class="bg-white prose brose-base flex flex-col flex-wrap text-black max-w-5xl w-full mx-auto py-8 md:py-12 lg:py-24 prose-p:mb-2 prose-p:mt-1 prose-h2:mb-2 prose-h3:mb-1 prose-h3:mt-3 prose-h4:mb-1 prose-h4:mt-0 prose-p:leading-6 prose-ul:my-0 prose-li:my-0 prose-li:marker:text-black px-6 md:px-12">

      <header class="flex max-md:flex-wrap items-end w-full border-b pb-4">
        <div class="flex-1">
          <h1 class="mb-0.5 font-medium text-5xl md:text-7xl leading-[0.9] tracking-tight">KRISTJAN <br> SUURSOHO</h1>
        </div>

        <div class="max-md:w-full flex flex-col md:items-end max-md:pt-6 pb-2">
          <span class="leading-6">Tallinn, Estonia</span>

          <a class="leading-6" target="_blank" href="https://www.linkedin.com/in/kristjan-suursoho-a475ba166/">
            LinkedIn
          </a>

          <a class="leading-6" href="mailto:kristjan.suursoho@gmail.com">
            kristjan.suursoho@gmail.com
          </a>
        </div>
      </header>

      <div class="py-4">
        <p class="opacity-90">
          Over the past decade, I've been helping different startups and development agencies develop strategies and
          execute their visions by designing and developing scalable and reliable solutions for various domains, like
          IoT systems, web/cloud platforms, and mobile apps. When I'm not deep in code, I recharge with piano/analog
          music or getting lost in art.
          <br>
          <br>
          I am currently freelancing and working on various projects, most of which focus on IoT and solution
          architecture.
        </p>
      </div>

      <section class="divide-y ">
        <h2 class="opacity-90 font-medium">Skills and ambitions</h2>

        <div class="flex flex-col gap-2 pt-2">
          <div v-for="skill in listOfSkills">
            <h3 class="opacity-90 font-medium">{{ skill.title }}</h3>
            <p>{{ skill.description }}</p>

            <div v-for="extra in skill.listOfExtra" class="pt-1 flex flex-wrap">
              <p class="mr-2 !mb-0 !mt-0">{{ extra.title }}</p>
              <p class="mr-2 !mb-0 !mt-0 italic" v-for="(item, index) in extra.list">
                <span>{{ item }}{{ index < extra.list.length - 1 ? ',' : '.' }}</span>
              </p>
            </div>
          </div>
        </div>
      </section>

      <section
        class="divide-y For the last decade or so I've been heavily involved with building start-ups or working with development agencies.">
        <h2 class="opacity-90 font-medium">Professional Experience</h2>
        <div class="flex flex-col gap-2 pt-2">
          <div v-for="experience in listOfExperience">
            <h3 class="opacity-90 font-medium">{{ experience.company }}</h3>
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

      <section
        class="divide-y For the last decade or so I've been heavily involved with building start-ups or working with development agencies.">
        <h2 class="opacity-90 font-medium">Testimonials</h2>
        <div class="flex flex-col gap-2 pt-2">
          <div v-for="testimonial in listOfTestimonial">
            <div class="flex max-sm:flex-col sm:items-end">
              <h3 class="opacity-90 font-medium">{{ testimonial.name }}</h3>
              <div class="flex-1"></div>
              <h4 class="sm:text-right">{{ testimonial.position }}</h4>
            </div>
            <p v-html="testimonial.text"></p>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup lang="ts">
const listOfSkills = [
  {
    title: 'IoT and Solution Architecture',
    description:
      'As a dedicated and detail-oriented professional, I am passionate about developing robust and cost-effective strategies using AWS services.',
    listOfExtra: [
      {
        title: 'Commonly used:',
        list: [
          'Terraform',
          'AWS IoT/Greengrass',
          'DynamoDB',
          'Lambda',
          'ECS',
          'VPC',
          'SQS',
          'S3',
          'Docker',
          'Timestream',
        ],
      },
    ],
  },
  {
    title: 'Full stack Development',
    description:
      'Im very eager to build and perfect various aspects of web applications, managmenent tools, micorservices or custom solutions.',
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
        list: ['c++', 'Rust', 'Java/Kotlin', 'Go'],
      },
    ],
  },

]

const listOfExperience = [
  {
    company: 'C-BOX',
    from: '2021',
    to: '2023',
    role: 'Lead developer & IoT engineer',
    devTeamSize: '1',
    listOfNote: [
      'Designed and developed end-to-end system for urban smart locker stations, ensuring reliable integration with various web and mobile solutions, utilizing AWS IoT Core, Greengrass, Python, SQS, MQTT, Rust, and TypeScript.',
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
