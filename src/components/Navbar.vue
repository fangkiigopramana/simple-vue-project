<template>
    <nav 
        :class="[`navbar-${theme}`,`bg-${theme}`, 'navbar navbar-expand-lg']"
    >
        <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page, index) in pages" class="nav-item" :key="index">
                    <navbar-link-vue
                        :page="page"
                        :is-active="index == activePage"
                        @click.prevent="navLinkClick(index)"
                    ></navbar-link-vue>
                </li>
            </ul>
            <form class="d-flex">
                <button 
                    class="btn btn-primary"
                    @click.prevent="changeTheme()">Toogle Navbar</button>
            </form>
        </div>
        </div>
    </nav>
</template>

<script>
import NavbarLinkVue from "./NavbarLink.vue";

export default {
    components: {
        NavbarLinkVue
    },
    props: ['pages', 'activePage', 'navLinkClick'],
    data(){
        return {
            theme: 'dark'
        }
    },
    methods: {
        changeTheme(){
            let theme = 'light';
            if (this.theme == 'light') {
                theme = 'dark';
            }
            this.theme = theme;
        }
    }
}
</script>