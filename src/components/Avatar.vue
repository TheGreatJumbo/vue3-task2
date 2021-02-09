<template>
    <div class="avatar">
        <img :src="url">
    </div>
</template>

<script>
    // https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png
    export default {
        name: "Avatar",
        props: {
            url: {
                type: String,
                required: true
            },
        }
    }
</script>

<style scoped>

</style>