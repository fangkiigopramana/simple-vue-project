<template>
    <nav 
        :class="[`navbar-${theme}`,`bg-${theme}`, 'navbar navbar-expand-lg custom-navbar sticky-top']" 
    >
        <div class="container">
            <a class="navbar-brand" href="#">Furni Store</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="custom-navbar-nav navbar-nav ms-auto mb-2 mb-md-0">
                    <li v-for="(page, index) in pages" class="nav-item" :key="index">
                        <navbar-link-vue
                            :page="page"
                            :is-active="index == activePage"
                            @click.prevent="navLinkClick(index)"
                        ></navbar-link-vue>
                    </li>
                </ul>
                <ul class="custom-navbar-cta navbar-nav mb-2 mb-md-0 ms-5">
                    <li>
                        <div class="dropdown text-end">
                            <a href="#" class="d-block link-body-emphasis text-decoration-none dropdown-toggle" data-bs-toggle="dropdown" aria-expanded="false">
                              <img src="https://github.com/mdo.png" alt="mdo" width="32" height="32" class="rounded-circle">
                            </a>
                            <ul class="dropdown-menu text-small">
                              <li><a class="dropdown-item" href="#">New project...</a></li>
                              <li><a class="dropdown-item" href="#">Settings</a></li>
                              <li><a class="dropdown-item" href="#">Profile</a></li>
                              <li><hr class="dropdown-divider"></li>
                              <li><a class="dropdown-item" href="#signout">Sign out</a></li>
                            </ul>
                          </div>
                    </li>
                    <li><a class="nav-link" href="cart.html"><img src="../assets/images/cart.svg" alt="Cart Image"></a></li>
                </ul>
                <ul class="custom-navbar-nav navbar-nav ms-auto mb-2 mb-md-0">
                    <li class="nav-item active">
                        <a class="nav-link fw-semibold fs-7" href="#login">Login</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link fw-semibold fs-7" href="#register">Register</a>
                    </li>
                </ul>
                <!-- <form class="d-flex">
                    <button 
                        class="btn btn-primary"
                        @click.prevent="changeTheme()">Toogle Navbar</button>
                </form> -->
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