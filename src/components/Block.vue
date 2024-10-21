<template>
    <div class="block" v-if="showBlock">
        Click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false
        }
    },
    mounted() {
        console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            console.log(this.delay)
        }, this.delay)
    },
    updated() {
        console.log('component updated')
    },
    unmounted() {
        console.log('unmounted')
    }
}
</script>

<style>
    .block {
        width: 25rem;
        border-radius: 1.25rem;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 2.5rem auto;
    }
</style>