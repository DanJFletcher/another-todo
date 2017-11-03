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
        <ul class="list-group">
            <li class="list-group-item" v-for="(value, index) in listItems" :key="index">
                <list-item :text="value" :id="index"></list-item>
            </li>
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
                text: '',
            }
        },

        created: function () {
            eventHub.$on('delete-list-item', this.deleteListItem)
        },

        methods: {
            addItem () {
                if (this.text.length > 0) {
                    this.listItems.unshift(this.text)
                }
                this.text = ''
            },

            deleteListItem (id) {
                this.listItems.splice(id, 1)
            }
        },
    }
</script>

<style>
    #todo-list {
        max-width: 400px;
    }
</style>