<template>
    <a 
        class="nav-link"
        :class="activeClasses"
        aria-current="page"
        :href="page.link.href"
        :title="`This link direct to ${page.link.href}`"
    > {{ page.link.text }}
    </a>
</template>

<script>

export default {
    props: ['page', 'isActive'],
    computed: {
        activeClasses(){
            return {
                active: this.isActive,
                emphatize: this.isActive
            }
        }
    }
}
</script>

<style scoped>
.emphatize{
    text-decoration: underline !important;
    font-weight: bold !important;
}
</style>