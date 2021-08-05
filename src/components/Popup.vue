<template>
    <div class="popup bg-white w-25 mx-auto align-self-center mt-5" v-show="true">
        <img src="../assets/x-circle-fill.svg" alt="" class="m-3 close">
        <slot></slot>
    </div>
</template>


<script>
    export default {
        name: 'Popup',
        methods: {
            
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .popup {
        position: fixed;
        left: 0;
        right: 0;
        border: 1px solid black;
    }

    .close {
        width: 6%;
        position: absolute;
        right: 0;
        cursor: pointer;
    }

    /*Animations */
</style>