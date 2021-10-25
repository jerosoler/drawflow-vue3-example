<template>
    <div class="header">{{title}}</div>
</template>
<script>
import { defineComponent } from 'vue'

export default defineComponent({
    props: ['title'],
})
</script>


<style scoped>
div {
    background: #494949;
    margin-top: -15px;
    margin-left: -15px;
    margin-right: -15px;
    padding: 10px 15px;
    margin-bottom: 15px;
}
</style>