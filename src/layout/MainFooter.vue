<template>
  <footer
    class="footer"
    :class="{ [`footer-${type}`]: type }"
    :data-background-color="backgroundColor"
  >
    <div class="container">
      <nav>
        <ul>
          <li>
            <a href="https://www.github.com" target="_blank">
              Documentação
            </a>
          </li>
          <li>
            <a href="https://www.github.com" target="_blank">
              Código
            </a>
          </li>
        </ul>
      </nav>
      <div class="copyright">
        &copy; {{ year }}, made with <md-icon>favorite</md-icon> by 
        <a class="user-github-link" href="https://github.com/GabrielPaliari" target="_blank">
          Gabriel Paliari
        </a>
      </div>
    </div>
  </footer>
</template>
<script>
export default {
  props: {
    backgroundColor: String,
    type: String
  },
  data() {
    return {
      year: new Date().getFullYear()
    };
  }
};
</script>
<style>
  .user-github-link {
    text-decoration: underline !important;
  }
</style>
