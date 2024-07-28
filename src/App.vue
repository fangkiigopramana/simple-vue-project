<template>
   <navbar-vue 
        :pages="pages"
        :active-page="activePage"
        :nav-link-click="(index) => activePage = index"
    ></navbar-vue>
    <content-vue
        :page="pages[activePage]"
    ></content-vue>
</template>

<script>
import ContentVue from "./components/Content.vue"
import NavbarVue from "./components/Navbar.vue"


export default {
  components: {
    ContentVue,
    NavbarVue
  },
  data(){
      return {
          activePage: 0,
          theme: 'light',
          pages: [
              {
                  link: {text:'Home', href:'index.html'},
                  pageTitle: 'Hello Home',
                  content: 'This is home page'
              },
              {
                  link: {text:'About', href:'about.html'},
                  pageTitle: 'Hello About',
                  content: 'This is about page'
              },
              {
                  link: {text:'Contact', href:'contact.html'},
                  pageTitle: 'Hello Contact',
                  content: 'This is contact page'
              },
          ]
      }
  },
}
</script>