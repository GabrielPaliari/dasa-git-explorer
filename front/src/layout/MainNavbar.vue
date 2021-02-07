<template>
  <md-toolbar
    id="toolbar"
    md-elevation="0"
    class="md-absolute"
    :class="{ [`md-${type}`]: type }"
  >
    <div class="md-toolbar-row md-collapse-lateral">
      <div class="md-toolbar-section-start">
        <img class="logo-dasa" :src="dasaLogo"/>
        <h3 class="brand-title">Hub</h3>
        <h4 class="brand-slogan">The Git Explorer</h4> 
      </div>
      <div class="md-toolbar-section-end">
        <md-button
          class="md-just-icon md-simple md-toolbar-toggle"
          :class="{ toggled: toggledClass }"
          @click="toggleNavbarMobile()"
        >
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </md-button>

        <div class="md-collapse">
          <div class="md-collapse-wrapper">
            <mobile-menu nav-mobile-section-start="false">
              <!-- Here you can add your items from the section-start of your toolbar -->
            </mobile-menu>
            <md-list>
              <md-list-item
                href="https://github.com/dasa-health/test-nac"
                target="_blank"
              >
                <i class="fab fa-github fa-lg"></i>
                <p>Código</p>
              </md-list-item>
              <md-list-item
                href="https://github.com/dasa-health/test-nac"
                target="_blank"
              >
                <i class="fas fa-book fa-lg"></i>
                <p>Documentação</p>
              </md-list-item>
            </md-list>
              
          </div>
        </div>
      </div>
    </div>
  </md-toolbar>
</template>

<script>
let resizeTimeout;
function resizeThrottler(actualResizeHandler) {
  // ignore resize events as long as an actualResizeHandler execution is in the queue
  if (!resizeTimeout) {
    resizeTimeout = setTimeout(() => {
      resizeTimeout = null;
      actualResizeHandler();

      // The actualResizeHandler will execute at a rate of 15fps
    }, 66);
  }
}

import MobileMenu from "@/layout/MobileMenu";
export default {
  components: {
    MobileMenu
  },
  props: {
    type: {
      type: String,
      default: "white",
      validator(value) {
        return [
          "white",
          "default",
          "primary",
          "danger",
          "success",
          "warning",
          "info"
        ].includes(value);
      }
    },
    dasaLogo: {
      type: String,
      default: require("@/assets/img/logo-dasa.png")
    }
  },
  data() {
    return {
      toggledClass: false
    }
  },
  methods: {
    bodyClick() {
      let bodyClick = document.getElementById("bodyClick");

      if (bodyClick === null) {
        let body = document.querySelector("body");
        let elem = document.createElement("div");
        elem.setAttribute("id", "bodyClick");
        body.appendChild(elem);

        let bodyClick = document.getElementById("bodyClick");
        bodyClick.addEventListener("click", this.toggleNavbarMobile);
      } else {
        bodyClick.remove();
      }
    },
    toggleNavbarMobile() {
      this.NavbarStore.showNavbar = !this.NavbarStore.showNavbar;
      this.toggledClass = !this.toggledClass;
      this.bodyClick();
    },
  },
};
</script>

<style lang="css">
  .logo-dasa {
    width: 120px;
    margin-top: -10px;
  }
  .brand-title {
    margin: 10px 10px 10px -12px;
    font-size: 22px;
  }
  .brand-slogan {
    font-size: 16px;
  }
</style>
