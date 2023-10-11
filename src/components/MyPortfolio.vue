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
          <a href="#" target="_blank" :style="{ '--i': 9 }">
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
          my text here jslkfjsdlkfjdsfj as part of a full stack testing sentence
          secret ambition etc. and i am the best one the can etc. hahaha
          sdlfkjsdl jsdlk sdlkj sdl kjsdj sdk jsd sdlfj sdjfsdl jsd
        </p>
        <a href="#" class="btn-box">More About Me</a>
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
                  :style="{ '--i': 11 }"
                >
                  <i class="bx bxl-facebook"></i>
                </a>
                <a href="#" :style="{ '--i': 12 }">
                  <i class="bx bxl-instagram"></i>
                </a>
                <a href="#" target="_blank" :style="{ '--i': 13 }">
                  <i class="bx bxl-github"></i>
                </a>
                <a href="#" :style="{ '--i': 14 }">
                  <i class="bx bxl-whatsapp"></i>
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