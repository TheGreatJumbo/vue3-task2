<template>
    <div class="container column">
        <Generator @CreateBlock="GenerateBlock"></Generator>
        <Constructor :Elements="Structure"></Constructor>
    </div>
    <div class="container">
        <p v-if="commentsStatus === 'hidden'">
            <button class="btn primary" @click="LoadComments">Загрузить комментарии</button>
        </p>
        <Loading v-if="commentsStatus === 'loading'"></Loading>
        <Alert v-if="commentsStatus === 'failed'" @TryAgain="LoadComments">{{error}}</Alert>
        <Comments :data="commentsData" v-if="commentsStatus === 'loaded'"></Comments>
    </div>
</template>

<script>
    import Generator from "./components/Generator";
    import Constructor from "./components/Constructor";
    import Comments from "./components/Comments";
    import Loading from "./components/Loading";
    import Alert from "./components/Alert";
    export default {
        components: {
            Generator,
            Constructor,
            Comments,
            Loading,
            Alert
        },
        data() {
            return {
                Structure: [],
                commentsData: {},
                commentsStatus: 'hidden',
                error: ''
            }
        },
        methods: {
            GenerateBlock(block, value) {
                this.Structure.push({
                    component: block,
                    content: value
                })
            },
            async LoadComments() {
                this.commentsStatus = 'loading'
                try {
                    let res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42');
                    if (res.ok) {
                        res.json().then(data => {
                            this.commentsData = data
                        })
                        this.commentsStatus = 'loaded'
                    }
                    else {
                        this.commentsStatus = 'failed'
                        this.error = 'Ошибка ' + res.status
                    }
                }
                catch (e) {
                    this.commentsStatus = 'failed'
                    this.error = e.message
                }
            }
        }
    }
</script>

<style>
    .avatar {
        display: flex;
        justify-content: center;
    }

    .avatar img {
        width: 150px;
        height: auto;
        border-radius: 50%;
    }
</style>
