<template>
  <div @click="closeNavBar">
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
        <a href="#todo-list" style="--i: 3">Todo</a>
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
        <p>
          Web Designer
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
          <a
            href="https://www.instagram.com/Followed%20by%20189%2C271%20people/?fbclid=IwAR1rIl4vpvTIqjXl609QXyz1_wab6kps5eDvR9mgJ7zxjTm8oEiiumflshs"
            :style="{ '--i': 8 }"
            target="_blank"
          >
            <i class="bx bxl-instagram"></i>
          </a>
          <a
            href="https://github.com/Daisylimpangog"
            target="_blank"
            :style="{ '--i': 9 }"
          >
            <i class="bx bxl-github"></i>
          </a>
          <a
            href="https://l.facebook.com/l.php?u=https%3A%2F%2Ftiktok.com%2F%40Followed%2520by%25201%252C723%252C927%2520people%3Ffbclid%3DIwAR0abiLyFwMObJ4R2EOOgY5ljn-tAzCMBOInWgFeZ0Q4uPnbxQxZUgu3iPU&h=AT1XEELZ7laqgf5RJFJJ1kij4qb_gxl3uFlvQtyd3421AQLALrLqZ-rsP7EMSO2kOotU_jUi_hVj43QRLkbPGsmrXunid0XYuzInqe2k8B9eWFaXAFp-Kvnh6U-TvZhSHrAC2OjtFPpByFiK3KGM"
            :style="{ '--i': 10 }"
            target="_blank"
          >
            <i class="bx bxl-tiktok"></i>
          </a>
        </div>
        <a href="#" class="btn-box">More About Me</a>
      </div>
      <div class="images">
        <img :src="daisy" />
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
          I am a 25-year-old male who consistently tells my teacher that I am a girl because my name is feminine, despite my actual gender being male. I have a strong inclination for social interaction, enjoying meeting new people and forming friendships. I am sociable, frequently going out with friends and family. Additionally, I have a passion for exploring new places, with a particular affinity for nature. I also have a keen interest in creative activities such as video and photo editing.
        </p>
        <a href="#" class="btn-box">More About Me</a>
      </div>
    </section>
    
    <section style="display: flex; height: 100vh;">
      <!-- <h1 className="sub-title" style="font-size: 50px; margin-bottom: -20px;">My <span>Skills</span></h1> -->
      <div class="container1" id="skills">
        <h1 class="heading1">My <span style="color: #0ef;">Skills</span></h1>
        <div class="technical-bars">
          <div v-for="(skill, index) in skills" :key="index" class="bar">
            <i :class="skill.iconClass" :style="{ color: skill.color }"></i>
            <div class="info">
              <span>{{ skill.name }}</span>
            </div>
            <div :class="['progress-line', skill.class]">
              <span></span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="todo-list">
      <div class="todo-container">
        <div class="todo-body">
          <h1>Todo List App</h1>
          <div class="input-list">
            <div class="search-list">
              <input
                type="text"
                v-model="searchText"
                placeholder="Search Todo..."
              />
              <i class="bx bx-search-alt-2"></i>
            </div>
          </div>
          <div v-for="(todo, index) in todos" :key="index" class="todo-list">
            <p>{{ todo.text }}</p>
            <i @click="removeTodo(index)" class="bx bx-x"></i>
          </div>

          <div class="add-todo">
            <h1>Add New List</h1>
            <div class="new-input">
              <input
                type="text"
                v-model="newTodo"
                placeholder="Write Here..."
              />
              <i @click="addTodo" class="bx bx-plus"></i>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section>
      <div id="contact">
        <div class="container">
          <div class="rowd">
            <div class="contact-left">
              <h1 class="sub-title">
                Contact <span style="color: #0ef">Me</span>
              </h1>
              <p class="emails">
                <i class="bx bx-send"></i> {{ contactEmail }}
              </p>
              <p><i class="bx bx-phone"></i> {{ contactPhoneNumber }}</p>
              <div class="home-sci">
                <a
                  href="https://www.facebook.com/daisy.jroa"
                  target="_blank"
                  :style="{ '--i': 7 }"
                >
                  <i class="bx bxl-facebook"></i>
                </a>
                <a
                  href="https://www.instagram.com/Followed%20by%20189%2C271%20people/?fbclid=IwAR1rIl4vpvTIqjXl609QXyz1_wab6kps5eDvR9mgJ7zxjTm8oEiiumflshs"
                  :style="{ '--i': 8 }"
                  target="_blank"
                >
                  <i class="bx bxl-instagram"></i>
                </a>
                <a
                  href="https://github.com/Daisylimpangog"
                  target="_blank"
                  :style="{ '--i': 9 }"
                >
                  <i class="bx bxl-github"></i>
                </a>
                <a
                  href="https://l.facebook.com/l.php?u=https%3A%2F%2Ftiktok.com%2F%40Followed%2520by%25201%252C723%252C927%2520people%3Ffbclid%3DIwAR0abiLyFwMObJ4R2EOOgY5ljn-tAzCMBOInWgFeZ0Q4uPnbxQxZUgu3iPU&h=AT1XEELZ7laqgf5RJFJJ1kij4qb_gxl3uFlvQtyd3421AQLALrLqZ-rsP7EMSO2kOotU_jUi_hVj43QRLkbPGsmrXunid0XYuzInqe2k8B9eWFaXAFp-Kvnh6U-TvZhSHrAC2OjtFPpByFiK3KGM"
                  :style="{ '--i': 10 }"
                  target="_blank"
                >
                  <i class="bx bxl-tiktok"></i>
                </a>
              </div>
              <a href="#" class="btn btn2">Download CV</a>
            </div>
            <div class="contact-right">
              <form @submit.prevent="submitForm">
                <input
                  type="text"
                  v-model="name"
                  placeholder="Your Name"
                  required
                />
                <input
                  type="email"
                  v-model="email"
                  placeholder="Your@gmail.com"
                  required
                />
                <textarea
                  v-model="message"
                  placeholder="Your Message"
                  cols="30"
                  rows="10"
                ></textarea>
                <button type="submit" class="btn btn2">Submit</button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div>
      <div class="last-text">
        <p>© Copyright 2023</p>
      </div>
    </div>
  </div>
</template>

<script>
import "../assets/css/Style.css";

// boxicons
import "boxicons/css/boxicons.min.css";

export default {
  data() {
    return {
      navBar: false,
      logo: require("../assets/images/logo.jpg"),
      daisy: require("../assets/images/daisy.jpg"),
      contactEmail: "Daisylimpangog@gmail.com",
      contactPhoneNumber: "09204890541",
      socialLinks: {
        facebook: "#",
        twitter: "#",
        instagram: "#",
        linkedin: "#",
      },
      name: "",
      email: "",
      message: "",
      searchText: "",
      newTodo: "",
      todos: [
        { text: "this is the list number 1" },
        {
          text: "this is the list nusdf sdf sdf sdf sdf dsf ds fdsf dsf dsfsd fds sdf sdf sdfmber 1",
        },
        { text: "this is the list number 1" },
      ],
      skills: [
        {
          name: "HTML",
          iconClass: "bx bxl-html5",
          color: "#c95d2e",
          class: "html",
        },
        {
          name: "CSS",
          iconClass: "bx bxl-css3",
          color: "#147bbc",
          class: "css",
        },
        {
          name: "Java",
          iconClass: "bx bxl-java",
          color: "#b0bc1e",
          class: "javascript",
        },
      ],
    };
  },
  methods: {
    toggleNavBar() {
      this.navBar = !this.navBar;
    },
    closeNavBar() {
      this.navBar = false;
    },
    submitForm() {
      // Handle form submission here
    },
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push({ text: this.newTodo });
        this.newTodo = "";
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>