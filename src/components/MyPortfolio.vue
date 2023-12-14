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
      <div class="home-content2">
        <h3>Hello, It's Me</h3>
        <h1>John Lloyd S. Rosales</h1>
        <p>Web Designer</p>

        <div class="home-sci">
          <a
            href="https://www.facebook.com/john.clair.28"
            target="_blank"
            :style="{ '--i': 2 }"
          >
            <i class="bx bxl-facebook"></i>
          </a>
          <a
            href="https://www.instagram.com/its_johnx/"
            :style="{ '--i': 8 }"
            target="_blank"
          >
            <i class="bx bxl-instagram"></i>
          </a>
          <a
            href="https://github.com/Rosales1124"
            target="_blank"
            :style="{ '--i': 9 }"
          >
            <i class="bx bxl-github"></i>
          </a>
          <a
            href="https://www.tiktok.com/@user492397399?lang=en"
            :style="{ '--i': 10 }"
            target="_blank"
          >
            <i class="bx bxl-tiktok"></i>
          </a>
        </div>
        <a href="about-text" class="btn-box">About Me</a>
      </div>
      <div class="images">
        <img :src="rosales" />
      </div>
      <span class="home-imgHover"></span>
    </section>

    <section class="about" id="about">
      <div class="about-img">
        <img :src="rosales" />
      </div>
      <div class="about-text">
        <h2>About <span>Me</span></h2>
        <h4>Who I Am</h4>
        <p>
          I am John Lloyd Rosales, 24 years old. I have four members in the family including myself, my mom and dad is a street vendor
          they give me a reason to study hard so that i can give back to them and give the life that they deserve. I am passionate and hardworking
          person, also I am friendly and helpful. In addition, I am an aspirant programmer, and hopefully i can claim myself as a programmer in the near future
        </p>
        <a href="#" class="btn-box">More About Me</a>
      </div>
    </section>

    <section style="display: flex; height: 100vh">
      
      <div class="container1" id="skills">
        <h1 class="heading1">My <span style="color: rgb(255, 0, 34)">Skills</span></h1>
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
      <div class="container2">
      <div class="title2"><h1>Todo App</h1></div>
      <div class="actions2">
        <form @submit="addTask">
          <input type="text" placeholder="Add Task" v-model="task" required />
          <button type="submit" class="add">Add</button>
          <div class="search">
            <input
              type="text"
              placeholder="Search task"
              v-model="searchTerm"
              @input="searchTask"
            />
          </div>
        </form>
      </div>
      <div class="tasks">
        <div class="task-items" v-for="todo in filteredTodos" :key="todo.id">
          <p :class="{ 'done-task': todo.status }">{{ todo.details }}</p>
          <button class="done-btn" @click="toggleTaskStatus(todo.id)">
            Done
          </button>
          <button class="remove-btn" @click="removeTask(todo.id)">Remove</button>
        </div>
        <button
          class="clear-btn"
          @click="clearAllTasks"
          v-show="todos.length > 0"
        >
          Clear Task
        </button>
      </div>
    </div>
    </section>
    <br>
    <br>
    <br>
      <section id="alarmclock">
        <h1 style="text-align: center; font-size: 30px;">Alarm Clock Application</h1>
        <br>
    <div class="container3">
      <h1>Alarm Clock</h1>
      <div class="clock">
        <div id="time"></div>
        <div id="date"></div>
      </div>
      <div class="controls">
        <label for="alarmTime">Set Alarm:</label>
        <input type="time" id="alarmTime" />
        <div class="btn2">
          <button @click="setAlarm" id="setAlarm">Set</button>
<button @click="clearAlarm">Clear</button>
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
                Contact <span style="color: rgb(123, 0, 255)">Me</span>
              </h1>
              <p class="emails">
                <i class="bx bx-send"></i> {{ contactEmail }}
              </p>
              <p><i class="bx bx-phone"></i> {{ contactPhoneNumber }}</p>
              <div class="home-sci">
                <a
                  href="https://www.facebook.com/john.clair.28"
                  target="_blank"
                  :style="{ '--i': 7 }"
                >
                  <i class="bx bxl-facebook"></i>
                </a>
                <a
                  href="https://www.instagram.com/its_johnx/"
                  :style="{ '--i': 8 }"
                  target="_blank"
                >
                  <i class="bx bxl-instagram"></i>
                </a>
                <a
                  href="https://github.com/Rosales1124"
                  target="_blank"
                  :style="{ '--i': 9 }"
                >
                  <i class="bx bxl-github"></i>
                </a>
                <a
                  href="https://www.tiktok.com/@user492397399?lang=en"
                  :style="{ '--i': 10 }"
                  target="_blank"
                >
                  <i class="bx bxl-tiktok"></i>
                </a>
              </div>
              <a href="#" class="btn btn2">Download CV</a>
            </div>
            <div class="container4">
  <form action="tambokpinoy22@gmail.com">

    <label for="fname">First Name</label>
    <input type="text" id="fname" name="firstname" placeholder="Your name..">

    <label for="lname">Last Name</label>
    <input type="text" id="lname" name="lastname" placeholder="Your last name..">

    <label for="country">Country</label>
    <select id="country" name="country">
      <option value="australia">Australia</option>
      <option value="canada">Canada</option>
      <option value="usa">USA</option>
    </select>

    <label for="subject">Subject</label>
    <textarea id="subject" name="subject" placeholder="Write something.." style="height:200px"></textarea>

    <input type="submit" value="Submit">

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

<style>
.completed {
  text-decoration: line-through; 
  text-align: center; 
}
</style>
<script>
import "../assets/css/Style.css";
import "boxicons/css/boxicons.min.css";
import { v4 as uuidv4 } from "uuid";

export default {
  data() {
    return {
      navBar: false,
      logo: require("../assets/images/logo.jpg"),
      rosales: require("../assets/images/rosales.jpg"),
      contactEmail: "tambokpinoy22@gmail.com",
      contactPhoneNumber: "09455898071",
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

      task: "",
      todos: [],
      searchTerm: "",
      foundTasks: [], // New property to store found tasks
    };
  },
  computed: {
    incompleteTodosExist() {
      return this.todos.some((todo) => !todo.completed || todo.completed);
    },
    filteredTodos() {
      return this.foundTasks.length > 0 ? this.foundTasks : this.todos;
    },
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
    toggleTaskStatus(id) {
      const task = this.todos.find((todo) => todo.id === id);
      if (task) {
        task.status = !task.status;
      }
    },
    addTask(e) {
      e.preventDefault();
      const newTask = {
        id: uuidv4(),
        details: this.task,
        status: false,
      };
      this.todos.unshift(newTask);
      this.task = "";
    },
    removeTask(id) {
      const index = this.todos.findIndex((todo) => todo.id === id);
      if (index !== -1) {
        this.todos.splice(index, 1);
      }
    },
    clearAllTasks() {
      this.todos = [];
    },
    searchTask() {
      this.foundTasks = this.todos.filter((todo) => {
        return todo.details
          .toLowerCase()
          .includes(this.searchTerm.toLowerCase());
      });
    },

    updateClock() {
      const now = new Date();
      const timeElement = document.getElementById("time");
      const dateElement = document.getElementById("date");

      const hours = now.getHours().toString().padStart(2, "0");
      const minutes = now.getMinutes().toString().padStart(2, "0");
      const seconds = now.getSeconds().toString().padStart(2, "0");
      const timeString = `${hours}:${minutes}:${seconds}`;

      const options = {
        weekday: "long",
        year: "numeric",
        month: "long",
        day: "numeric",
      };
      const dateString = now.toLocaleDateString("en-US", options);

      timeElement.textContent = timeString;
      dateElement.textContent = dateString;
    },

    setAlarm() {
      const alarmTimeInput = document.getElementById("alarmTime");
      const alarmTime = alarmTimeInput.value;

      if (alarmTime) {
        const now = new Date();
        const alarmDateTime = new Date(now.toDateString() + " " + alarmTime);

        const timeDifference = alarmDateTime - now;

        if (timeDifference > 0) {
          setTimeout(() => {
            alert("Alarm!");
          }, timeDifference);
        } else {
          alert("Please set a future time for the alarm.");
        }
      } else {
        alert("Please set a time for the alarm.");
      }
    },

    clearAlarm() {
      const alarmTimeInput = document.getElementById("alarmTime");
      alarmTimeInput.value = "";
    },
  },
  mounted() {
    setInterval(this.updateClock, 1000);
    this.updateClock();
  },
};
</script>