<template>
    <div>
        <li class="list-group-item">{{ text }}</li>
    </div>
</template>

<script>
export default {
    props: {
        text: {
            type: String,
            required: true
        }
    }
}
</script>
