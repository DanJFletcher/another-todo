<template>
    <div id="todo-list" class="center-block">
        <div class="panel panel-default">
        <!-- Default panel contents -->
        <div class="panel-heading">Todo List</div>
        <div class="panel-body">
            <div class="input-group">
                <input 
                    type="text" 
                    class="form-control" 
                    placeholder="Something to do..."
                    v-model="text"
                    @keyup.enter="addItem">
                <span class="input-group-btn">
                    <button 
                        class="btn btn-primary" 
                        type="button" 
                        @click="addItem">Add</button>
                </span>
            </div><!-- /input-group -->
        </div>

        <!-- List group -->
        <ul class="list-group" v-for="listItem in listItems" v-bind:key="listItem">
            <list-item :text="listItem"></list-item>
        </ul>
        </div>
    </div>
</template>

<script>
    import ListItem from './list-item'
    export default {
        components: {
            'list-item': ListItem
        },

        data () {
            return {
                listItems: ['fuck', 'shit', 'balls'],
                text: ''
            }
        },

        methods: {
            addItem () {
                this.listItems.unshift(this.text)
                this.text = ''
            }
        }
    }
</script>

<style>
    #todo-list {
        max-width: 400px;
    }
</style>