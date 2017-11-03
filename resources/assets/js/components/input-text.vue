<template>
    <input 
        type="text" 
        :class="classes" 
        placeholder="Something to do..."
        v-model="text"
        @keyup.enter="addItem"
        @keyup="updateText">
</template>

<script>
    export default {
        props: {
            classes: [String, Array],
            placeholder: String
        },

        data () {
            return {
                text: ''
            }
        },

        methods: {
            addItem () {
                eventHub.$emit('add-list-item')
                this.text = ''
            },

            updateText () {
                eventHub.$emit('update-text', (this.text))
            }
        }
    }
</script>