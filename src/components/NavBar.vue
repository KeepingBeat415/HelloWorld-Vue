<template>
  <nav :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My Vue</a>
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li v-for="(page, index) in pages" class="nav-item" :key="index">
          <!-- <a
            class="nav-link"
            :class="{ active: activePage == index }"
            aria-current="page"
            :href="page.link.url"
            :title="`This link goes to the ${page.link.text} page`"
            @click.prevent="navLinkClick(index)"
          >
            {{ page.link.text }}
          </a> -->
          <navbar-link :page="page" :isActive="activePage === index" @click.prevent="navLinkClick(index)">
          </navbar-link>
        </li>
      </ul>
      <from class="d-flex">
        <button class="btn btn-primary" @click.prevent="changeTheme()">Toggle</button>
      </from>
    </div>
  </nav>
</template>

<script>
import NavbarLink from './NavbarLink.vue';

export default {
  components: {
    NavbarLink,
  },
  created() {
    // this.getThemeSetting();
  },
  props: ['pages', 'activePage', 'navLinkClick'],
  data() {
    return {
      theme: 'light',
    };
  },
  method: {
    changeTheme() {
      let theme = 'light';
      if (this.theme == 'light') {
        theme = 'dark';
      }
      this.theme = theme;
      this.storeThemeSetting();
    },
    storeThemeSetting() {
      localStorage.setItem('theme', this.theme);
    },
    getThemeSetting() {
      let theme = localStorage.getItem('theme');

      if (theme) {
        this.theme = theme;
      }
    },
  },
};
</script>

<style scoped>
.emphasize {
  text-decoration: underline !important;
}
</style>
