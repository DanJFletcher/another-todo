<template>
    <span class="input-group-btn">
        <button 
            class="btn btn-primary" 
            type="button" 
            @click="addListItem">Add</button>
    </span>
</template>

<script>
    export default {
        methods: {
            addListItem () {
                eventHub.$emit('add-list-item')
            }
        }
    }
</script>