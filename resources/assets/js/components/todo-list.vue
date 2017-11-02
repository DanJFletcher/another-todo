<template>
    <div id="todo-list" class="center-block">
        <div class="panel panel-default">
        <!-- Default panel contents -->
        <div class="panel-heading">Todo List</div>
        <div class="panel-body">
            <div class="input-group">
                <input type="text" class="form-control" placeholder="Something to do...">
                <span class="input-group-btn">
                    <button class="btn btn-primary" type="button">Add</button>
                </span>
            </div><!-- /input-group -->
        </div>

        <!-- List group -->
        <ul class="list-group">
            <li class="list-group-item">Cras justo odio</li>
            <li class="list-group-item">Dapibus ac facilisis in</li>
            <li class="list-group-item">Morbi leo risus</li>
            <li class="list-group-item">Porta ac consectetur ac</li>
            <li class="list-group-item">Vestibulum at eros</li>
        </ul>
        </div>
    </div>
</template>

<script>
    export default {}
</script>

<style>
    #todo-list {
        max-width: 400px;
    }
</style>