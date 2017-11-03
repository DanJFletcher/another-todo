<template>
    <div>
        <li class="list-group-item">
            <div class="row">
                <div class="col-md-2">
                    <input @click="checkListItem" type="checkbox" aria-label="...">
                </div>
                <div class="col-md-10">
                    <span class="text" v-bind:class="{ checked: isChecked }">
                        {{ text }}
                    </span>
                </div>
            </div>
        </li>
    </div>
</template>

<script>
export default {
    props: {
        text: {
            type: String,
            required: true
        }
    },

    data () {
        return {
            isChecked: false
        }
    },

    methods: {
        checkListItem () {
            this.isChecked = ! this.isChecked
        }
    }
}
</script>

<style>

    .checked { text-decoration: line-through; }

</style>
