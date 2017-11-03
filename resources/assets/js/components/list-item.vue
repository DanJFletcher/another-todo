<template>
    <div class="row">
        <div class="col-md-2">
            <input @click="checkListItem" type="checkbox" aria-label="...">
        </div>
        <div class="col-md-8">
            <span class="text" v-bind:class="{ checked: isChecked }">
                {{ text }}
            </span>
        </div>
        <div class="col-md-2">
            <span @click="deleteListItem" class="close">X</span>
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
        id: Number
    },

    data () {
        return {
            isChecked: false,
            deleteed: false
        }
    },

    methods: {
        checkListItem () {
            this.isChecked = ! this.isChecked
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
