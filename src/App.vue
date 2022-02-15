<template>
  <div>
    <Navbar />
    <section
      id="main"
      data-bs-spy="scroll"
      data-bs-target="#navbar-example2"
      data-bs-offset="0"
      class="scrollspy-example header-me"
      tabindex="0"
    >
      <div class="info-header__me animate__animated animate__zoomInDown">
        <h1>
          Hola,
          <br />Soy
          <b style="color: #fff;">Angel Mora</b>
        </h1>
        <h2>Desarrollador web</h2>
        <ul class="links-social__contact">
          <li>
            <a
              href="https://www.linkedin.com/in/angel-mora-a1a959207/"
              rel="noopener noreferrer"
              title="linkedin"
              target="_blank"
              data-bs-toggle="tooltip"
              data-bs-placement="bottom"
            >
              <i class="fab fa-linkedin"></i>
            </a>
          </li>
          <li>
            <a
              href="https://github.com/AngelMApps"
              rel="noopener noreferrer"
              title="github"
              target="_blank"
              data-bs-toggle="tooltip"
              data-bs-placement="bottom"
            >
              <i class="fab fa-github"></i>
            </a>
          </li>
          <li>
            <a
              href="mailto: angel456mora123@gmail.com"
              rel="noopener noreferrer"
              title="correo"
              target="_blank"
              data-bs-toggle="tooltip"
              data-bs-placement="bottom"
            >
              <i class="fas fa-envelope"></i>
            </a>
          </li>
          <li>
            <a
              href="https://api.whatsapp.com/send/?phone=+51983785116&text&app_absent=0"
              rel="noopener noreferrer"
              title="whatsapp"
              target="_blank"
              data-bs-toggle="tooltip"
              data-bs-placement="bottom"
            >
              <i class="fab fa-whatsapp"></i>
            </a>
          </li>
        </ul>
      </div>
      <img
        class="avatar animate__animated animate__fadeInDown animate__slow"
        src="./assets/portfolio/profile.jpg"
        alt="avatar"
      />
    </section>
    <section
      id="sobre-mi"
      data-bs-spy="scroll"
      data-bs-target="#navbar-example2"
      data-bs-offset="0"
      class="scrollspy-example section-sobre__mi"
      tabindex="0"
    >
      <h2 class="fade_left">¿Quién Soy?</h2>
      <hr />
      <p>
        <b>Me llamo Angel Mora, tengo 18 años y soy un desarrollador web de Lima - Perú.</b>
        <br />Estoy
        interesado en ayudarte a impulsar y hacer crecer tu idea o negocio con el
        <br />desarrollo de una
        página web única y llamativa para las personas
        <br />y
        que este disponible en diferentes tipos de dispositivos.
      </p>
      <img
        class="avatar"
        src="./assets/portfolio/yo.jpeg"
        alt="avatar"
      />
    </section>
    <section
      id="mi-skills"
      data-bs-spy="scroll"
      data-bs-target="#navbar-example2"
      data-bs-offset="1"
      class="scrollspy-example section-mi__skills"
      tabindex="1"
    >
      <h2 class="fade_left">My Skills</h2>
      <hr />
      <div class="container">
        <div class="row">
          <div
            class="card card-skills col-6 col-sm-3 col-md-4"
            v-for="(skill, index) in skills"
            :key="index"
          >
            <div class="card-body">
              <img :src="skill.icon"  :alt="skill.name" />
              <h5 class="card-title">{{ skill.name }}</h5>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section
      id="mi-projects"
      data-bs-spy="scroll"
      data-bs-target="#navbar-example2"
      data-bs-offset="2"
      class="scrollspy-example section-mi__projects"
      tabindex="2"
    >
      <h2 class="fade_left">Mis Projectos</h2>
      <hr />
      <div class="container">
        <div class="row" style="--bs-gutter-x: 0rem;">
          <div
            class="card card-project col-6 col-sm-3 col-md-4"
            v-for="(project, index) in projects"
            :key="index"
          >
            <img :src="project.ProjectImage" class="card-img-top" alt="image" />
            <div class="card-body">
              <h5 class="card-title">{{ project.ProjectName }}</h5>
              <p class="card-text">{{ project.ProjectDescription }}</p>
              <div class="card-footer">
                <a
                  :href="project.ProjectURL"
                  rel="noopener noreferrer"
                  title="{{project.ProjectName}}"
                  target="_blank"
                >
                  <i class="fas fa-external-link-alt"></i>
                </a>
                <a
                  :href="project.ProjectCode"
                  rel="noopener noreferrer"
                  title="{{project.ProjectName}}"
                  target="_blank"
                >
                  <i class="fab fa-github"></i>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import { onMounted, reactive } from "vue";
import axios from 'axios';
export default {
  name: "App",
  components: {
    Navbar
  },
  setup() {
    let projects = reactive([]);
    let skills = [
      {
        'name': 'css',
        'icon': require('./assets/portfolio/css.png'),
      }, {
        'name': 'django',
        'icon': require('./assets/portfolio/django.png'),
      }, {
        'name': 'firebase',
        'icon': require('./assets/portfolio/firebase.png'),
      }, {
        'name': 'git',
        'icon':  require('./assets/portfolio/git.png'),
      }, {
        'name': 'github',
        'icon': require('./assets/portfolio/github.png'),
      }, {
        'name': 'html',
        'icon': require('./assets/portfolio/html.png'),
      }, {
        'name': 'javascript',
        'icon': require('./assets/portfolio/js.png'),
      }, {
        'name': 'mongodb',
        'icon': require('./assets/portfolio/mongodb.png'),
      }, {
        'name': 'python',
        'icon': require('./assets/portfolio/python.png'),
      }, {
        'name': 'sass',
        'icon': require('./assets/portfolio/sass.png'),
      }, {
        'name': 'svelte',
        'icon': require('./assets/portfolio/svelte.png'),
      },{
        'name': 'VueJS',
        'icon': require('./assets/portfolio/vue.png'),
      }, {
        'name': 'vscode',
        'icon': require('./assets/portfolio/vscode.png'),
      },
    ]
    onMounted(() => {
      axios.get('https://backend-angelmora-portafolio.herokuapp.com/projects')
        .then((response) => {
          response.data.forEach(element => {
            projects.push(element);
          });
        });
    })
    return {
      publicPath: process.env.BASE_URL,
      projects,
      skills,
    }
  }
};
</script>

<style lang="scss">
body {
  background: #202020;
}

hr,
hr:not([size]) {
  height: 3px;
  background: #5c7c9c;
  background: linear-gradient(90deg, #5c7c9c 0, #40679c 43%, #3f13c4 100%);
  width: 30%;
}

.transform_left {
  transform: translateX(-100%);
}

ul {
  margin: 0;
  margin-block: 0;
  margin-inline: 0;
  padding: 0;
  padding-inline: 0;
}

.avatar {
  width: 350px;
  height: 350px;
  border-radius: 999px;
  margin: 10px;
}

.header-me {
  width: 100%;
  height: 45rem;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
}

.info-header__me {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

h1,
h2 {
  font-family: Oswald, cursive, Raleway, sans-serif;
}

.info-header__me h1,
.info-header__me h2 {
  text-align: left;
  font-family: Oswald, cursive, Raleway, sans-serif;
}

.info-header__me h1 {
  color: #6a7acf;
  font-size: 60pt;
}

.info-header__me h2 {
  margin-top: 10px;
  color: #5969bb;
  font-size: 60pt;
}

.info-header__me ul,
.links-social__contact {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  list-style: none;
  margin: 0;
  margin-block: 0;
  margin-inline: 0;
  padding: 0;
  padding-inline: 0;
  width: 100%;
}

.info-header__me ul a {
  text-decoration: none;
  text-align: center;
  background-color: transparent;
  font-family: Oswald, cursive, Raleway, sans-serif;
  color: #7d75f7;
  width: 7rem;
  height: 7rem;
  font-size: 30pt;
  transition: color 1s, font-size 0.5s ease-in-out;
}

.info-header__me ul a:hover {
  color: #dddbff;
  font-size: 32pt;
  transition: color 1s, font-size 0.5s ease-in-out;
}

.section-sobre__mi {
  padding: 4rem 0;
  display: flex;
  height: 50rem;
  text-align: center;
  color: #fff;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow-wrap: break-word;
}
.card-footer{
  width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}
.section-sobre__mi h2 {
  opacity: 0.5;
  transition: all 0.5s;
  color: #6a7acf;
  font-size: 50pt;
}

.section-sobre__mi p {
  font-size: 17pt;
}

.section-mi__skills {
  padding: 4rem 0;
  display: flex;
  text-align: center;
  color: #fff;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow-wrap: break-word;
}

.section-mi__skills h2 {
  opacity: 0.5;
  transition: all 0.5s;
  color: #8192e6;
  font-size: 50pt;
}

.section-mi__skills img {
  height: 100px;
}

.card {
  background-color: rgba(0, 0, 0, 0.178);
  margin: 1.5rem 0.5rem;
}

.card-skills {
  width: 13rem;
}

.row {
  justify-content: center;
}

.card-title {
  color: #fff;
  margin-top: 1rem;
}

.card-body {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.section-mi__projects {
  background-color: transparent;
  padding: 4rem 0;
  display: flex;
  text-align: center;
  color: #fff;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow-wrap: break-word;
}

.section-mi__projects h2 {
  opacity: 0.5;
  transition: all 0.5s;
  color: #8192e6;
  font-size: 50pt;
}

.card-project {
  width: 15rem;
}

.section-mi__projects img {
  height: 8rem;
}

.section-mi__projects a {
  text-decoration: none;
  text-align: center;
  background-color: transparent;
  color: #7d75f7;
  font-size: 20pt;
  transition: color 1s, font-size 0.5s ease-in-out;
}

.section-mi__projects a:hover {
  color: #dddbff;
  font-size: 21pt;
  transition: color 1s, font-size 0.5s ease-in-out;
}

.aparecer {
  opacity: 1 !important;
  transform: none;
}

@media screen and (max-width: 950px) {
  .header-me {
    height: 60rem;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
  }
}

@media screen and (max-width: 903px) {
  .section-sobre__mi p {
    font-size: 14pt;
  }
}

@media screen and (max-width: 740px) {
  .section-sobre__mi p {
    padding: 0 1.4rem;
    font-size: 12pt;
  }
}

@media screen and (max-width: 599px) {
  .header-me {
    height: 46rem;
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  .info-header__me h1,
  .info-header__me h2 {
    text-align: left;
    font-size: 50pt;
    font-family: Oswald, cursive, Raleway, sans-serif;
  }
  .info-header__me ul,
  .links-social__contact {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    list-style: none;
    margin: 0;
    margin-block: 0;
    margin-inline: 0;
    padding: 0;
    padding-inline: 0;
    width: 100%;
  }
}

@media screen and (max-width: 510px) {
  .header-me {
    height: 36rem;
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  .info-header__me h1,
  .info-header__me h2 {
    text-align: left;
    font-size: 40pt;
    font-family: Oswald, cursive, Raleway, sans-serif;
  }
  .info-header__me ul,
  .links-social__contact {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    list-style: none;
    margin: 0;
    margin-block: 0;
    margin-inline: 0;
    padding: 0;
    padding-inline: 0;
    width: 100%;
  }
  .header-me img {
    width: 250px;
    height: 250px;
  }
}

@media screen and (max-width: 420px) {
  .info-header__me h1,
  .info-header__me h2 {
    text-align: left;
    font-size: 30pt;
    font-family: Oswald, cursive, Raleway, sans-serif;
  }
  .info-header__me ul,
  .links-social__contact {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    list-style: none;
    margin: 0;
    margin-block: 0;
    margin-inline: 0;
    padding: 0;
    padding-inline: 0;
    width: 100%;
  }
}

@media (max-width: 380px) {
  .header-me {
    height: 34rem;
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  .section-sobre__mi h2 {
    font-size: 40pt;
  }
  .section-sobre__mi img {
    width: 310px;
    height: 310px;
  }
}

@media (max-width: 340px) {
  .header-me {
    height: 34rem;
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  .section-sobre__mi h2 {
    font-size: 40pt;
  }
  .section-sobre__mi img {
    width: 230px;
    height: 230px;
  }
}

@media (max-width: 318px) {
  .header-me {
    height: 40rem;
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  .info-header__me h1,
  .info-header__me h2 {
    text-align: left;
    font-size: 25pt;
    font-family: Oswald, cursive, Raleway, sans-serif;
  }
  .info-header__me ul,
  .links-social__contact {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    list-style: none;
    margin: 0;
    margin-block: 0;
    margin-inline: 0;
    padding: 0;
    padding-inline: 0;
    width: 100%;
  }
  .header-me img {
    width: 230px;
    height: 230px;
  }
}

@media (max-width: 304px) {
  .section-mi__projects h2 {
    font-size: 35pt;
  }
}

@media (max-width: 285px) {
  .header-me {
    height: 28rem;
    margin-top: 5rem;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  .section-sobre__mi h2 {
    font-size: 40pt;
  }
  .section-sobre__mi img {
    width: 230px;
    height: 230px;
  }
}
</style>
