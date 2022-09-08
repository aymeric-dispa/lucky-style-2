<template>
  <nav id="navbar-example2" class="navbar navbar-expand-lg fixed-top navbar-light px-3 bg-dark"
       :class="{'bg-white':scrollPosition >= 0,'bg-transparent':scrollPosition < 1}">
    <div class="container-fluid" id="yo">
      <a class="navbar-brand" href="#">Lucky Style<span style="font-size: 85%; text-align: center; color: gray">&nbsp;&nbsp;0497/318099</span></a>

      <a href="https://www.facebook.com/LUCKYzSTYLE/" target="_blank">
        <img class="icon" src="../assets/facebook.svg"></a>
      <button class="navbar-toggler bg-white" style="background-color: white;" type="button" data-bs-toggle="collapse"
              data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
              aria-label="Toggle navigation">
        <span class="navbar-toggler-icon bg-white " style="background-color: white;"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ml-auto text-center ms-auto bg">
          <li class="nav-item">
            <a class="nav-link" aria-current="page" href="#a-propos">À propos</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#pricing">Tarifs</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <div data-bs-spy="scroll" data-bs-target="#navbarSupportedContent" class="scrollspy-example" tabindex="0">
    <HeaderDog id="headerDog"></HeaderDog>
    <Presentation id="a-propos"></Presentation>
    <Pricing id="pricing"></Pricing>
    <Contact id="contact"/>
  </div>
</template>
<script>
import Presentation from "./About";
import HeaderDog from "./HeaderDog";
import Pricing from "@/components/Pricing";
import Contact from "./Contact";

export default {
  data: function () {
    return {
      scrollPosition: 0
    }
  },
  methods: {
    handleScroll() {
      this.scrollPosition = window.scrollY
    }

  },
  components: {
    Contact,
    Pricing,
    Presentation, HeaderDog
  },

  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    // I switched the example from `destroyed` to `beforeDestroy`
    // to exercise your mind a bit. This lifecycle method works too.
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style scoped>
#navbar-example2 {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: right;
  font-size: 140%;
  color: white;
  position: fixed;
  width: 100%;
  z-index: 99999;
  padding-bottom: 0;
}

@media only screen and (max-width: 992px) {
  .navbar-collapse {
    background: #ffffff;
  }
}

</style>
