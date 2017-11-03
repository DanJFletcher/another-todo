<template>
    <div class="row">
        <div class="col-xs-2">
            <input @click="checkListItem" type="checkbox" aria-label="...">
        </div>
        <div class="col-xs-8">
            <span class="text" v-bind:class="{ checked: checked }">
                {{ text }}
            </span>
        </div>
        <div class="col-xs-2">
            <button @click="deleteListItem" type="button" class="close" aria-label="Close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            text: {
                type: String,
                required: true
            },
            id: String
        },

        data () {
            return {
                checked: false
            }
        },

        methods: {
            checkListItem () {
                this.checked = ! this.checked
                eventHub.$emit('toggle-list-item', this.id)
            },

            deleteListItem () {
                eventHub.$emit('delete-list-item', this.id)
            }
        }
    }
</script>

<style>

    .checked { text-decoration: line-through; }

</style>
