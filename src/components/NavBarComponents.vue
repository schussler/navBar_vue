<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <img
          src="https://bulma.io/images/bulma-logo.png"
          width="112"
          height="28"
        />
      </a>
      <!-- MENU BURGUER -->
      <a
        @click="toggleMenu()"
        role="button"
        class="navbar-burger"
        aria-label="menu"
        aria-expanded="false"
        data-target="navbarBasicExample"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navBar-itens" class="navbar-menu">
      <div class="navbar-start">
        <router-link class="navbar-item" to="/">Home</router-link>

        <router-link class="navbar-item" to="/about">About</router-link>
      </div>
    </div>

    <div v-if="showMenu" class="navBar-itens-burguer">
      <div class="navbar-start">
        <router-link class="navbar-item" to="/">inicio</router-link>

        <router-link class="navbar-item" to="/about">sobre</router-link>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      showMenu: false,
    };
  },
  mounted() {
    window.addEventListener("resize", this.handleResize);
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
    },
    handleResize() {
      // Defina showMenu como false quando a tela for redimensionada
      this.showMenu = false;
    },
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.handleResize);
  },
};
</script>

<style scoped>
nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.navBar-itens-burguer {
  background-color: #f1f1f1;
  border: 1px solid #ccc;
  position: absolute;
  top: 50px; /* ou ajuste conforme necessário */
  left: 0;
  width: 100%;
  z-index: 1000;
}
</style>
