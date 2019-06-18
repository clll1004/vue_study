<template>
    <button class="clear_btn" @click="passClear" :disabled="clearAvail">
        <i class="fa fa-bomb"></i>
    </button>
</template>

<script>
export default {
    props: ['clearAvail'],
    methods: {
        passClear() {
            this.$emit('passClear');
        }
    }
}
</script>

<style scoped>
    .clear_btn {
        width: 5rem;
        margin-top: 40px;
        border: none;
        border-radius: 5px;
        outline: none;
        cursor: pointer;
        background: rgba(0,0,0,0);
    }
    .clear_btn i {
        height: 50px;
        line-height: 50px;
        font-size: 25px;
        color: #f1f7e6;
    }
    .clear_btn:disabled {
        cursor: initial;
    }
    .clear_btn:disabled i {
        color: #ddd;
    }
</style>

