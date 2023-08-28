<template>
    <div id="app">
        <HeaderWeb />
        <nuxt />
        <FooterWeb />
    </div>
</template>

<script>
import HeaderWeb from "../components/headerWeb.vue"
import FooterWeb from "../components/footerWeb.vue"
export default {
    components: {
        HeaderWeb,
        FooterWeb
    }
}
</script>