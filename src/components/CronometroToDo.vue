<template>
    <section class="time-box">
        <strong class="timer">{{time}}</strong>
    </section>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'

    export default defineComponent({
        name: 'CronometroToDo', 
        props: {
            seconds: {
                type: Number,
                default: 0
            }
        },

        computed: {
            time() : string {
                return new Date(this.seconds * 1000).toISOString().substr(11,8)
            }
        },
    })
</script>

<style>
.box .column, .lista strong{
    color: #ffffff !important;
}
</style>