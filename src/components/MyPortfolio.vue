<template>
  <div>
    <header class="header">
      <div class="react-icon" @click="toggleNavBar" style="cursor: pointer">
        <i class="iconBar" v-if="!navBar" @click.stop="toggleNavBar">☰</i>
        <i class="iconBar" v-else @click.stop="toggleNavBar">×</i>
      </div>
      <a href="#" class="logo"></a>
      <img :src="logo" class="myLogo logo" />
      <nav
        class="navbar"
        :style="{
          width: navBar ? '200px' : '',
          padding: navBar ? '50px 50px 0px 0px' : '0',
        }"
      >
        <a href="#" style="--i: 1" class="active">Home</a>
        <a href="#about" style="--i: 2">About</a>
        <a href="#skills" style="--i: 3">Skill</a>
        <a href="#contact" style="--i: 5">Contact</a>
        <a href="#" v-show="navBar" class="fast" @click="closeNavBar"
          ><i class="i">×</i></a
        >
      </nav>
    </header>

    <section class="home">
      <div class="home-content">
        <h3>Hello, It's Me</h3>
        <h1>Daisy A. Limpangog</h1>
        <h3>
          And I'm a <span class="text">{{ currentString }}</span>
        </h3>
        <p>
          Web Developer etc.
          <br />expertise is to create a website design etc. not yet
        </p>

        <div class="home-sci">
          <a
            href="https://www.facebook.com/daisy.jroa"
            target="_blank"
            :style="{ '--i': 7 }"
          >
            <i class="bx bxl-facebook"></i>
          </a>
          <a href="#" :style="{ '--i': 8 }">
            <i class="bx bxl-instagram"></i>
          </a>
          <a
            href="#"
            target="_blank"
            :style="{ '--i': 9 }"
          >
            <i class="bx bxl-github"></i>
          </a>
          <a href="#" :style="{ '--i': 10 }">
            <i class="bx bxl-whatsapp"></i>
          </a>
        </div>
        <a href="#" class="btn-box">More About Me</a>
      </div>
      <div class="images">
        <img :src="s" />
      </div>
      <span class="home-imgHover"></span>
    </section>

    <section class="about" id="about">
    <div class="about-img">
      <img :src="daisy" />
    </div>
    <div class="about-text">
      <h2>About <span>Me</span></h2>
      <h4>Who I Am</h4>
      <p>
        my text here jslkfjsdlkfjdsfj as part of a full stack testing sentence secret ambition etc. and i am the
        best one the can etc. hahaha sdlfkjsdl jsdlk sdlkj sdl kjsdj sdk jsd sdlfj sdjfsdl jsd
      </p>
      <a href="#" class="btn-box">More About Me</a>
    </div>
  </section>
  </div>
</template>

<script>
import "../assets/css/Style.css";

// boxicons
import 'boxicons/css/boxicons.min.css';

export default {
  data() {
    return {
      navBar: false,
      logo: require("../assets/images/logo.jpg"),
      daisy: require("../assets/images/daisy.jpg"),
    };
  },
  methods: {
    toggleNavBar() {
      this.navBar = !this.navBar;
    },
    closeNavBar() {
      this.navBar = false;
    },
  },
};
</script>

<style scoped>
/* Add component-specific styles here */
</style>
