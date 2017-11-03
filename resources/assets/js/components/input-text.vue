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

        created () {
            eventHub.$on('clear-text', this.clearText)
        },

        methods: {
            addItem () {
                eventHub.$emit('add-list-item')
            },

            updateText () {
                eventHub.$emit('update-text', (this.text))
            },

            clearText () {
                this.text = ''
            }
        }
    }
</script>