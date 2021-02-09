<template>
    <div class="card">
        <h2>Комментарии</h2>
        <ul class="list" v-for="comment in data">
            <li class="list-item">
                <div>
                    <p><strong>{{comment.email}}</strong></p>
                    <small>{{comment.body}}</small>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "Comments",
        props: {
            data: {
                type: Object,
                required: true
            },
        }
    }
</script>

<style scoped>

</style>