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
            <li class="list-group-item" v-for="listItem in listItems" :key="listItem.id">
                <list-item :text="listItem.text" :id="listItem.id"></list-item>
            </li>
        </ul>
        </div>
    </div>
</template>

<script>
    import ListItem from './list-item'
    import uuidv1 from 'uuid/v1'

    export default {
        components: {
            'list-item': ListItem
        },

        data () {
            return {
                listItems: [],
                text: '',
            }
        },

        created: function () {
            eventHub.$on('delete-list-item', this.deleteListItem)
        },

        methods: {
            addItem () {
                if (this.text.length > 0) {
                    this.listItems.unshift({id: uuidv1(), text: this.text})
                }
                this.text = ''
            },

            deleteListItem (id) {
                this.listItems = this.listItems.filter(function (item) {
                    return item.id !== id
                })
            }
        },
    }
</script>

<style>
    #todo-list {
        max-width: 400px;
    }
</style>