<template>
    <div class="container">
        <div>
            <h1 class="title">nuxt</h1>
            <div class="links">
                <nuxt-link to="/help" class="button--green"
                    >gsap, tailwind</nuxt-link
                >
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style>
.container {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    margin: 0 auto;
    text-align: center;
}

.title {
    display: block;
    color: #35495e;
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system,
        BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial,
        sans-serif;
    font-size: 100px;
    font-weight: 300;
    letter-spacing: 1px;
}

.links {
    padding-top: 15px;
}
</style>
