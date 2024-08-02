<template>
   <Navbar
        :pages="pages"
        :active-page="activePage"
        :nav-link-click="(index) => activePage = index"/>
    <!-- <Content :page="pages[activePage]"/> -->
    <div v-if="activePage == 0">
        <Home />
    </div>
    <div v-else-if="activePage == 1">
        <Shop />
    </div>
    <div v-else>
        <About />
    </div>
</template>

<script>
import Navbar from "./components/Navbar.vue"
import Content from "./components/Content.vue"
import Shop from "./pages/Shop.vue"
import About from "./pages/About.vue"
import Home from "./pages/Home.vue"


export default {
  components: {
    Navbar,
    Content,
    Shop,
    About,
    Home
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
                  link: {text:'Shop', href:'shop.html'},
                  pageTitle: 'Hello About',
                  content: 'This is about page'
              },
              {
                  link: {text:'About', href:'about.html'},
                  pageTitle: 'Hello Contact',
                  content: 'This is contact page'
              },
          ]
      }
  },
}
</script>