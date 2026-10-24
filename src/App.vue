<script setup lang="ts">
 
import { onMounted, ref } from 'vue'

const showIntro = ref(true)
const loadingProgress = ref(0)

const roles = ['STUDENT', 'CREATIVE THINKER', 'COMPUTER ENGINEERING']
const roleIndex = ref(0)

function changeRole() {
  roleIndex.value = (roleIndex.value + 1) % roles.length
}
const skills = [
  {
    category: 'Web Development',
    items: ['-HTML ', 
            '-CSS ', 
            '-JavaScript ',
            '-Vue.js ',
            '-TypeScript '],
  },
  {
    category: 'Hardware & Electronics',
    items: [
      '-PCB Design ',
      '-Basic Electronics ',
      '-Digital Logic Design ', 
      '-Circuit Analysis ',
    ],
  },
  {
    category: 'Robotics & Embedded Systems',
    items: [
      '-Robotics ',
      '-Line Follower ',
      '-Microcontrollers ',
      '-Sensor Integration ',
    ],
  },
  {
    category: 'Tools & Technologies',
    items: [
      '-VS Code ',
      '-Git & GitHub ',
      '-Proteus ',
      '-PostgreSQL ',
    ],
  },
  {
    category: 'Professional Skills',
    items: [
      '-Problem-Solving ',
      '-Teamwork ',
      '-Critical Thinking ',
      '-Leadership ',
    ],
  },
]

const projects = [
  {
    number: '01',
    title: 'EduMart',
    category: 'Thesis',
    status: 'In Progress',
    description: 'A digital marketplace project currently under development.',
    src: '',
  },
  {
    number: '02',
    title: 'Binary Calculator',
    category: 'Logic Circuit Design',
    status: 'Completed',
    description: 'A project showcasing my skills in logic circuit design.',
    src: '/binary_calculator.jpg',
  },
  {
    number: '03',
    title: 'PCB Design',
    category: 'CEDAD',
    status: 'Completed',
    description: 'A project showcasing my skills in printed circuit board design.',
    src: '/pcb.jpg',
  },
  {
    number: '04',
    title: 'Regional Competition (RegCon)',
    category: 'Robotics (Line Follower)',
    status: '4th Place',
    description: 'A project showcasing my skills in robotics and engineering.',
    src: '/regcon.jpg',
  },
  {
    number: '05',
    title: 'ITE Regional',
    category: 'Regional Competition',
    status: 'Champion',
    description: 'A regional competition for Robotics(Linefollower).',
    src: '/ite_regional.jpg',
  },
]


onMounted(() => {
  const interval = window.setInterval(() => {
    loadingProgress.value = Math.min(
      loadingProgress.value + 5,
      100,
    )

    if (loadingProgress.value >= 100) {
      window.clearInterval(interval)

      window.setTimeout(() => {
        showIntro.value = false
      }, 100)
    }
  }, 30)
})

</script>

<template>
  <div>
    <!-- INTRO ANIMATION -->
    <Transition name="intro">
      <div v-if="showIntro" class="intro-screen">
        <div class="intro-content">
          <p class="intro-label">JEROME BAQUIRAN PAGARAN </p>

          <h1 class="intro-title">
            WELCOME<span>.</span>
          </h1>

          <p class="intro-status">INITIALIZING PORTFOLIO...</p>

          <div class="loading-track">
            <div
              class="loading-progress"
              :style="{ width: loadingProgress + '%' }"
            ></div>
          </div>

          <p class="loading-number">
            {{ loadingProgress }}% <span>LOADING</span>
          </p>
        </div>
      </div>
    </Transition>

    <!-- MAIN PORTFOLIO -->
    <div class="portfolio">
      <header class="navbar">
        <a class="logo" href="#home">JBP<span>.</span></a>

        <nav>
          <a href="#home">HOME</a>
          <a href="#about">ABOUT</a>
          <a href="#skills">SKILLS</a>
          <a href="#projects">PROJECTS</a>
          <a href="#contact">CONTACT</a>
        </nav>

        <a class="nav-cta" href="#contact">LET'S TALK ↗</a>
      </header>

      <main>
        <!-- HERO -->
        <section id="home" class="hero section home-reveal">
          <div class="hero-copy">
            <p class="eyebrow">
              <span class="status-dot"></span>
              AVAILABLE FOR OPPORTUNITIES
            </p>

            <h1>
              JEROME<br />
              <span class="gradient-text">BAQUIRAN</span><br />
              PAGARAN<span class="accent">.</span>
            </h1>

            <div class="role-line">
              <span class="role-prefix">CURRENT MODE //</span>
              <button class="role-button" @click="changeRole">
                {{ roles[roleIndex] }} ↻
              </button>
            </div>

            <div class="hero-actions">
              <a class="button button-primary" href="#projects">
                EXPLORE MY WORK ↘
              </a>
              <a class="button button-outline" href="#about">
                DISCOVER MORE
              </a>
              
              <a
                  class="button button-outline"
                  href="/cv.jpg"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                 VIEW MY CV ↗
                </a>

                <a
                class="button button-primary"
                href="/cv.jpg"
                download="cv.jpg"
                >
               DOWNLOAD MY CV ↓
              </a>

             </div>

              </div>

          <div class="hero-visual">
            <div class="visual-grid"></div>
            <div class="portrait-card">
              <img 
                  class="profile-photo"
                  src="/jerome.jpg"
                  alt="Jerome Pagaran"
              />
             
              <span class="portrait-label"> Hello, I'm Jerome!</span>
            </div>

          </div>

        </section>

        
<!-- ABOUT -->
<section id="about" class="section content-section">
  <div class="about-layout">

    <!-- LEFT SIDE -->
    <div class="about-heading-block">
      <p class="eyebrow">ABOUT ME</p>

      <h2 class="about-heading">
        <span class="gradient-text typing-line">WHO I AM</span>
      </h2>
    </div>

    <!-- RIGHT SIDE: PHOTO AND INTRODUCTION -->
    <div class="about-profile">
      <div class="about-photo-container">
        <img
          class="about-profile-photo"
          src="/pagaran.jpg"
          alt="Jerome B. Pagaran"
        />
      </div>

      <div class="about-bio">
        <span class="portrait-label"></span>  
        <p class="soft-copy">
          I'm Jerome B. Pagaran from Tumauini, Isabela. taking
          Bachelor of Science in Computer Engineering at Cagayan State
          University - Carig Campus. I have a passion for software,
          hardware, and AI, creating innovative solutions that bridge
          the gap between technology and human experience. My hobbies
          include playing video games and listening to music, especially
          when going to sleep. I'm also a student leader. I enjoy turning
          ideas into digital experiences. My goal is to create websites
          that are functional, visually striking, and easy to use.
          This portfolio is my space to experiment, learn, and build
          what's next.
        </p>
      </div>
    </div>

  </div>
</section>


        <section class="section content-section">
          <p class="eyebrow">EDUCATION</p>
          <h2>
            LEARNING AND GROWING.<br />
            <span class="gradient-text">EVERY STEP OF THE WAY.</span>
          </h2>

          <div class="education-grid">
            <div class="education-card">
              <h3>CAGAYAN STATE UNIVERSITY - CARIG CAMPUS</h3>
              <p>Bachelor of Science in Computer Engineering</p>
              <p>2025 - Present</p>
            </div>

            <div class="education-card">
              <h3>UNIVERSITY OF CAGAYAN VALLEY</h3>
              <p>Bachelor of Science in Computer Engineering</p>
              <p>2022 - 2024</p>
            </div>

            <div class="education-card">
              <h3>TUMAUINI STAND-ALONE SENIOR HIGH SCHOOL</h3>
              <p>Senior High School</p>
              <p>2021 - 2022</p>
            </div>

            <div class="education-card">
              <h3>TUMAUINI NATIONAL HIGH SCHOOL</h3>
              <p>Junior High School</p>
              <p>2016 - 2021</p>
            </div>

            <div class="education-card">
              <h3>BAYABO EAST INTEGRATED SCHOOL</h3>
              <p>Elementary School</p>
              <p>2009 - 2016</p>
            </div>
          </div>
        </section>
        <!-- SKILLS -->
        <section id="skills" class="section content-section">
          <p class="eyebrow"> MY SKILLS</p>
          <h2>
            TOOLS OF THE <span class="gradient-text">TRADE.</span>
          </h2>

         <div class="skills-grid">
  <div
    v-for="group in skills"
    :key="group.category"
    class="skill-card"
  >
    <h3>{{ group.category }}</h3>

    <div class="skill-tags">
      <span
        v-for="skill in group.items"
        :key="skill"
      >
        {{ skill }}
      </span>
    </div>
        </div>
        </div>
        </section>
        <!-- PROJECTS -->
        <section id="projects" class="section content-section">
          <p class="eyebrow"> PROJECTS</p>
          <h2>
            IDEAS INTO <span class="gradient-text">REALITY.</span>
          </h2>

          
<div
  
  v-for="project in projects"
  :key="project.number"
  class="project-card"
>
  <div class="project-info">
    <!-- Existing project number -->
    <span class="project-number">
      {{ project.number }}
    </span>

    <h3>{{ project.title }}</h3>

    <p class="project-category">
      {{ project.category }}
    </p>

    <p class="project-description">
      {{ project.description }}
    </p>
  </div>

  <!-- Project image on the right -->
  <div class="project-image">
    <img
      v-if="project.src"
      :src="project.src"
      :alt="project.title"
      loading="lazy"
    />

    <div v-else class="project-placeholder">
      <span>PROJECT PREVIEW</span>
      <strong>COMING SOON</strong>
    </div>
  </div>
</div>
        </section>

        <!-- CONTACT -->
        <section id="contact" class="section contact-section">
          <p class="eyebrow"> YOUR MOVE</p>
          <h2>
            HAVE AN IDEA?<br />
            <span class="gradient-text">LET'S BUILD IT.</span>
          </h2>

          <p class="muted-copy">
            Have a project, collaboration, or opportunity in mind?
            Let's connect.
          </p>

          <a
            class="button button-primary"
            href="mailto:jeromebpagaran18@gmail.com"
          >
            SEND A MESSAGE ↗
          </a>

          <p class="small-note">
            LET'S CREATE SOMETHING AMAZING TOGETHER.
          </p>
        </section>
      </main>

      <!-- FOOTER -->
      <footer class="footer">
        <a class="logo" href="#home">JB<span>.</span></a>
        <p>DESIGNED WITH CURIOSITY. BUILT WITH CODE.</p>
        <a href="#home">BACK TO TOP ↑</a>    
      </footer>

      
<div class="social-links">
  <a
    href="https://www.facebook.com/jerome.Bpagaran.71"
    target="_blank"
    rel="noopener noreferrer"
    aria-label="Facebook"
  >
    Facebook ↗
  </a>

  <a
    href="https://www.instagram.com/omieee_69/"
    target="_blank"
    rel="noopener noreferrer"
    aria-label="Instagram"
  >
    Instagram ↗
  </a>
</div>

    </div>
  </div>
</template>
