<template>
    <div id="todo-list" class="center-block">
        <div class="panel panel-default">
            <div class="panel-heading">Todo List</div>
                <div class="panel-body">
                    <div class="input-group">
                        <input-text
                            classes="form-control"
                            placeholder="Somthing to do..."
                            v-model="text"
                        >
                        </input-text>
                        <add-list-item></add-list-item>
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
    </div>
</template>

<script>
    import AddListItem from './add-list-item'
    import ListItem from './list-item'
    import InputText from './input-text'
    import uuidv1 from 'uuid/v1'

    export default {
        components: {
            'list-item': ListItem,
            'input-text': InputText,
            'add-list-item': AddListItem
        },

        data () {
            return {
                listItems: [],
                text: ''
            }
        },

        created: function () {
            eventHub.$on('delete-list-item', this.deleteListItem)
            eventHub.$on('add-list-item', this.addListItem)
            eventHub.$on('update-text', this.updateText)
        },

        methods: {
            addListItem () {
                if (this.text.length > 0) {
                    this.listItems.unshift({id: uuidv1(), text: this.text})
                }
                eventHub.$emit('clear-text')
            },

            deleteListItem (id) {
                this.listItems = this.listItems.filter(function (item) {
                    return item.id !== id
                })
            },

            updateText (text) {
                this.text = text
            }
        },
    }
</script>

<style>
    #todo-list {
        max-width: 400px;
    }
</style>