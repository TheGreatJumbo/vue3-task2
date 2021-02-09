<template>
    <div class="card card-w70">
        <component v-if="Elements.length !== 0" v-for="E in Elements" :is="E.component"
                   v-bind="E.component === 'Avatar' ? {url: E.content} : {text: E.content}"></component>
        <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
</template>

<script>
    import MainTitle from "./MainTitle";
    import Avatar from "./Avatar";
    import Subtitle from "./Subtitle";
    import Text from "./Text";
    export default {
        name: "Constructor",
        components: {
            MainTitle,
            Avatar,
            Subtitle,
            Text
        },
        props: {
            Elements: {
                type: Array,
                required: true
            },
        },
    }
</script>

<style scoped>

</style>