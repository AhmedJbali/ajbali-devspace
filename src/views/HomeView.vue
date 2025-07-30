<template>
  <div class="container-fluid overflow-hidden">
    <div class="row g-0">
      <!-- Partie gauche avec photo + infos -->
      <aside class="col-md-3 col-lg-2 profile-sidebar">
        <div class="row g-0">
          <div class="col-12 text-center">
            <img src="@/assets/profile.jpg" alt="Ahmed Jbali" class="profile-image img-fluid" />
          </div>
          <div class="col-12 contact-info px-3">
            <p><strong>Email:</strong>ahmedjbali86@gmail.com</p>
            <p><strong>Téléphone:</strong> +216 52 419 334</p>
            <p><strong>LinkedIn:</strong>
              <a href="https://www.linkedin.com/in/ahmed-jbali-a8508319b/" target="_blank" rel="noopener noreferrer">
                linkedin.com/in/ahmedjbali
              </a>
            </p>
            <button @click="downloadCV" class="download-btn btn w-100">Télécharger CV PDF</button>
          </div>
        </div>
      </aside>

      <!-- Partie droite : contenu principal + menu -->
      <main class="col-md-9 col-lg-10 main-content">
        <div class="row g-0">
          <div class="col-12 px-3">
            <section
              id="profile"
              class="section fade-in-section"
              ref="profileSection"
            >
              <h2 class="section-title">Profil</h2>
              <p>
                Développeur Full Stack depuis 3 ans, dédié à la création d'applications web robustes et évolutives.
                Passionné par les nouvelles technologies, je perfectionne constamment mes compétences pour contribuer à
                des projets innovants grâce à ma détermination et ma créativité.
              </p>
            </section>
          </div>

          <div class="col-12 px-3">
            <section
              id="experience"
              class="section resume-area fade-in-section"
              ref="experienceSection"
            >
              <h2 class="section-title">Expérience Professionnelle</h2>
              <div class="resume-content">
                <div class="resume-timeline">
                  <div
                    class="item"
                    v-for="(exp, index) in experiences"
                    :key="index"
                    :class="index % 2 === 0 ? 'slide-from-left' : 'slide-from-right'"
                  >
                    <h3>{{ exp.title }}</h3>
                    <p><em>{{ exp.date }}</em></p>
                    <ul>
                      <li v-for="(point, idx) in exp.details" :key="idx">{{ point }}</li>
                    </ul>
                  </div>
                </div>
              </div>
            </section>
          </div>

          <div class="col-12 px-3">
            <section
              id="projects"
              class="section fade-in-section"
              ref="projectsSection"
            >
              <h2 class="section-title">Projets Professionnels</h2>
              <p>
                 Environnements : VueJS, Laravel, vue-router, Laravel-mix, Html, Css, Sass, REST API <br>
                Gestion des commandes avec VueJS, Laravel, REST API. Création d'une application moderne et responsive
                avec gestion des articles, panier, validation et suivi des commandes.
              </p>
            </section>
          </div>

          <div class="col-12 px-3">
            <section
              id="skills"
              class="section fade-in-section"
              ref="skillsSection"
            >
              <h2 class="section-title">Compétences</h2>
              <div class="row skills-list g-3 mx-0">
                <div 
                  class="col-6 col-sm-4 col-md-3 col-lg-2"
                  v-for="(skill, idx) in skills" 
                  :key="idx"
                >
                  <li class="skill-item">
                    <div class="skill-icon-circle">
                      <!-- Icône Devicon -->
                      <i :class="skill.iconClass" class="skill-icon"></i>
                    </div>
                    <span class="skill-name">{{ skill.name }}</span>
                  </li>
                </div>
              </div>
            </section>
          </div>
        </div>
      </main>

      <!-- Menu fixe à droite -->
      <nav class="side-menu">
        <ul>
          <li><a href="#profile" title="Profil"><i class="las la-user"></i></a></li>
          <li><a href="#experience" title="Expérience"><i class="las la-briefcase"></i></a></li>
          <li><a href="#projects" title="Projets"><i class="las la-stream"></i></a></li>
          <li><a href="#skills" title="Compétences"><i class="las la-shapes"></i></a></li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      experiences: [
        {
          title: "Développeur Full Stack - Eventizer",
          date: "Août 2022 – Mars 2025",
          details: [
            "Développement full stack d'applications web avec Angular et Laravel.",
            "Optimisation des performances, validation technique, debugging efficace.",
            "Méthodologie Agile (Scrum) : daily, sprint planning, retrospective."
          ]
        },
        {
          title: "Développeur WordPress CMS - Eventizer",
          date: "Mars 2025 – Juillet 2025",
          details: [
            "Déploiement de projets WordPress sur serveur Plesk.",
            "Création de modules dynamiques, automatisations et export de données.",
            "Conception d'interfaces responsive et pages multimédia."
          ]
        },
        {
          title: "Stagiaire - Lasser informatique",
          date: "Février 2020 – Juin 2020",
          details: [
            "Développement d'une application pharmaceutique ASP.NET avec Laravel.",
            "Intégration template responsive, connexion à base SQL Server."
          ]
        },
        {
          title: "Stagiaire - KeyObject",
          date: "Août 2019 – Septembre 2019",
          details: [
            "Développement d'une application web ASP.NET pour gestion bibliothèque en ligne."
          ]
        }
      ],
      skills: [
        { name: "Laravel", iconClass: "devicon-laravel-plain colored" },
        { name: "Angular", iconClass: "devicon-angularjs-plain colored" },
        { name: "Vue.js", iconClass: "devicon-vuejs-plain colored" },
        { name: "WordPress CMS", iconClass: "devicon-wordpress-plain colored" },
        { name: "PHP", iconClass: "devicon-php-plain colored" },
        { name: "JavaScript", iconClass: "devicon-javascript-plain colored" },
        { name: "MySQL", iconClass: "devicon-mysql-plain colored" },
        { name: "PostgreSQL", iconClass: "devicon-postgresql-plain colored" }
      ]
    };
  },
  mounted() {
    const sections = [
      this.$refs.profileSection,
      this.$refs.experienceSection,
      this.$refs.skillsSection,
      this.$refs.projectsSection
    ];

    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("is-visible");

            if (entry.target.id === "experience") {
              const items = entry.target.querySelectorAll(".item");
              items.forEach((item, idx) => {
                setTimeout(() => {
                  item.classList.add("visible");
                }, idx * 300);
              });
            }
          }
        });
      },
      { threshold: 0.3 }
    );
    sections.forEach((sec) => observer.observe(sec));
  },
  methods: {
    downloadCV() {
      const url = "/ajbali-devspace/cv/Ahmed_Jbali_CV.pdf";
      const link = document.createElement("a");
      link.href = url;
      link.download = "Ahmed_Jbali_CV.pdf";
      link.click();
    }
  }
};
</script>

<style scoped>
@import url("https://cdn.jsdelivr.net/npm/line-awesome@1.3.0/dist/line-awesome/css/line-awesome.min.css");
@import url('https://cdn.jsdelivr.net/gh/devicons/devicon@v2.15.1/devicon.min.css');
@import url('https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css');

/* Suppression des scrollbars */
html, body {
  overflow: hidden;
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}

.container-fluid {
  height: 100vh;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #0f172a;
  color: #cbd5e1;
  padding: 0;
  overflow: hidden;
}

/* Sidebar gauche */
.profile-sidebar {
  background-color: #1e293b;
  padding: 40px 0;
  height: 100vh;
  overflow-y: auto;
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

.profile-sidebar::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Opera */
}

.profile-image {
  width: 160px;
  height: 160px;
  border-radius: 50%;
  object-fit: contain;
  border: 3px solid #22c55e;
  margin-bottom: 20px;
}

.contact-info {
  width: 100%;
  padding: 0 15px;
}

.contact-info p {
  margin: 6px 0;
  font-size: 14px;
  word-wrap: break-word;
  text-align: left;
}

.contact-info a {
  color: #22c55e;
  text-decoration: none;
}

.contact-info a:hover {
  text-decoration: underline;
}

.download-btn {
  margin-top: 12px;
  background-color: #22c55e;
  color: #0f172a;
  font-weight: 700;
  border: none;
  padding: 10px 18px;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.download-btn:hover {
  background-color: #16a34a;
}

/* Contenu principal */
.main-content {
  padding: 40px 15px;
  height: 100vh;
  overflow-y: auto;
  position: relative;
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

.main-content::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Opera */
}

/* Sections */
.section {
  margin-bottom: 48px;
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}

.section.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.section-title {
  font-size: 2.5rem;
  color: #22c55e;
  margin-bottom: 16px;
  border-bottom: 3px solid #22c55e;
  padding-bottom: 4px;
  font-weight: 700;
}

/* Timeline expérience */
.resume-area .resume-content .resume-timeline {
  position: relative;
  border-left: 3px solid #22c55e;
  padding-left: 24px;
  margin-top: 24px;
}

.resume-area .resume-content .resume-timeline .item {
  position: relative;
  margin-bottom: 32px;
  padding-left: 12px;
  opacity: 0;
  transform: translateX(0);
  transition: none;
}

/* Cercles sur timeline */
.resume-area .resume-content .resume-timeline .item::before {
  content: '';
  position: absolute;
  width: 14px;
  height: 14px;
  background: #22c55e;
  border-radius: 50%;
  left: -10px;
  top: 6px;
  transition: 0.3s;
}

/* Animation entrée depuis gauche */
.slide-from-left {
  transform: translateX(-50px);
}

.slide-from-left.visible {
  animation: slideInLeft 0.8s ease forwards;
}

/* Animation entrée depuis droite */
.slide-from-right {
  transform: translateX(50px);
}

.slide-from-right.visible {
  animation: slideInRight 0.8s ease forwards;
}

/* Animation keyframes */
@keyframes slideInLeft {
  0% {
    opacity: 0;
    transform: translateX(-50px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  0% {
    opacity: 0;
    transform: translateX(50px);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Liste compétences */
.skills-list {
  list-style: none;
  padding-left: 0;
  margin: 0;
}

.skill-item {
  text-align: center;
  color: #aab2bd;
  font-weight: 600;
  margin-bottom: 20px;
  padding: 0 5px;
}

.skill-icon-circle {
  width: 80px;
  height: 80px;
  margin: 0 auto 8px;
  border-radius: 50%;
  background-color: #1f2937;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid #22c55e;
  transition: transform 0.3s ease;
}

.skill-icon-circle:hover {
  transform: scale(1.15);
  border-color: #16a34a;
}

.skill-icon {
  font-size: 48px;
  color: #22c55e;
}

/* Menu latéral droit */
.side-menu {
  position: fixed;
  top: 20vh;
  right: 20px;
  width: 60px;
  background-color: #1e293b;
  border-radius: 12px;
  box-shadow: 0 0 8px #22c55e;
  padding: 8px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 1000;
}

.side-menu ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.side-menu ul li {
  margin: 16px 0;
}

.side-menu ul li a {
  display: flex;
  justify-content: center;
  align-items: center;
  color: #22c55e;
  font-size: 28px;
  text-decoration: none;
  transition: color 0.3s;
  width: 44px;
  height: 44px;
  border-radius: 10px;
}

.side-menu ul li a:hover {
  background-color: #16a34a;
  color: white;
}

.devicon.colored {
  color: inherit !important;
}

/* Responsive adjustments */
@media (max-width: 767.98px) {
  .profile-sidebar {
    height: auto;
    padding: 20px;
  }
  
  .main-content {
    height: auto;
    padding: 20px;
  }

  .section-title {
    font-size: 1.8rem;
  }
  
  .skill-icon-circle {
    width: 60px;
    height: 60px;
  }
  
  .skill-icon {
    font-size: 36px;
  }

  #skills {
    margin-bottom: 240px;
  }
}

@media (min-width: 768px) and (max-width: 1026.98px) {
  #skills {
    margin-bottom: 560px;
  }
}
</style>