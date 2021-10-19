<template>
    <button
        class="btn"
        :style="{background: color}"
        @click="onClick()" 
    >
        {{ label }}
    </button>
</template>

<script>
    export default {
        name: "Button",
        props: {
            label: String,
            color: String,
        },
        methods: {
            onClick() {
                console.log("click");
            }
        }
    }
</script>