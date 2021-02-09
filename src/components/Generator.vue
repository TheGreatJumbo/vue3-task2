<template>
    <form class="card card-w30" @submit.prevent="CreateBlock">
        <div class="form-control">
            <label for="type">Тип блока</label>
            <select id="type" v-model="block">
                <option value="MainTitle">Заголовок</option>
                <option value="Subtitle">Подзаголовок</option>
                <option value="Avatar">Аватар</option>
                <option value="Text">Текст</option>
            </select>
        </div>
        <div class="form-control">
            <label for="value">Значение</label>
            <textarea id="value" rows="3" v-model="value"></textarea>
        </div>

        <button class="btn primary" :disabled="value.length < 4">Добавить</button>
    </form>
</template>

<script>
    export default {
        name: "Generator",
        emits: {
            CreateBlock(b, v) {
                if (b === '') {
                    console.warn('Block is not selected')
                    return false
                }
                else if (v === '') {
                    console.warn('Empty text value')
                    return false
                }
                else return true
            }
        },
        data() {
            return {
                block: 'MainTitle',
                value: '',
            }
        },
        methods: {
            CreateBlock() {
                this.$emit('CreateBlock', this.block, this.value)
                this.block = 'MainTitle'
                this.value = ''
            },
        },
    }
</script>

<style scoped>

</style>