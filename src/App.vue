<template>
  <nav-bar :pages="pages" :active-page="activePage" :nav-link-click="(index) => (activePage = index)"> </nav-bar>

  <!-- <page-viewer v-if="pages.length > 0" :page="pages[activePage]"> </page-viewer> -->
  <create-page :page-created="pageCreated"> </create-page>
</template>

<script>
import NavBar from './components/NavBar.vue';
// import PageViewer from './components/PageViewer.vue';
import CreatePage from './components/CreatePage.vue';

export default {
  components: {
    NavBar,
    // PageViewer,
    CreatePage,
  },
  created() {
    this.getPages();
  },
  data() {
    return {
      activePage: 0,

      pages: [
        // {
        //   link: { text: 'Home', url: 'index.html' },
        //   pageTitle: 'Home Page',
        //   content: 'This is the home content',
        // },
        // {
        //   link: { text: 'About', url: 'about.html' },
        //   pageTitle: 'About Page',
        //   content: 'This is the about content',
        // },
        // {
        //   link: { text: 'Contact', url: 'contact.html' },
        //   pageTitle: 'Contact Page',
        //   content: 'This is the contact content',
        // },
      ],
    };
  },
  methods: {
    // async getPages() {
    //   let res = await fetch('pages.json');
    //   let data = await res.json();

    //   return data;
    // },

    async getPages() {
      let res = await fetch('pages.json');
      let data = await res.json();

      this.pages = data;
    },
    pageCreated(pageObj) {
      console.log(pageObj);
    },
  },
};
</script>
