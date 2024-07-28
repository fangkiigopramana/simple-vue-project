<template>
    <div id="content" class="container">
        <h1 class="emphatize"> {{page.pageTitle}} </h1>
        <p> {{page.content}} </p> 
    </div>
</template>

<script>
export default {
    props: ['page']
}
</script>