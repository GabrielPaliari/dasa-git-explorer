<template>
  <div class="wrapper">
    <div class="section page-header header-filter" :style="headerStyle">
      <div class="background-filter-overlay"></div>
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-33 md-small-size-66 md-xsmall-size-100 md-medium-size-40 mx-auto"
          >
            <login-card header-color="primary">
              <h5 slot="title" class="card-title">Entre com o github:</h5>
              <md-button
                slot="buttons"
                href="javascript:void(0)"
                class="login-btn md-simple md-white md-lg"
              >
                <i class="fab fa-github fa-lg"></i>
                <span class="login-btn__text">Entrar</span>
              </md-button>
              <p slot="description" class="description">
                Faça o Login com o github para começar a explorar os repositórios
              </p>
            </login-card>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { LoginCard } from "@/components";

export default {
  components: {
    LoginCard
  },
  bodyClass: "login-page",
  data() {
    return {
      firstname: null,
      email: null,
      password: null
    };
  },
  props: {
    header: {
      type: String,
      default: require("@/assets/img/medical-programmer.jpg")
    }
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`
      };
    }
  }
};
</script>

<style lang="css">
  .wrapper {
    height: 100vh;
  }
  .background-filter-overlay {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: #182792b3;
  }
  .login-btn__text {
    margin-left: 8px;
  }
</style>
