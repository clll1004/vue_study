<template>
    <textarea title="view_area" id="view" @keydown="resize()" @keyup="resize()" placeholder="여기에 입력하세요." autofocus></textarea>
</template>

<script>
import EventBus from './EventBus.vue';
export default {
    methods: {
        resize() {
            document.getElementById('view').style.height = '1px';
            document.getElementById('view').style.height = document.getElementById('view').scrollHeight + "px";
        }
    },
    mounted() {
        EventBus.$on('sendInfo', (info) => {
            document.getElementById('view').style.fontFamily = info.family;
            document.getElementById('view').style.fontSize = info.size;
            document.getElementById('view').style.color = info.color;
            this.resize();
        });
    }
}
</script>

<style lang="scss" scoped>
    textarea {
        width: 100%;
        min-height: 100px;
        padding: 15px;
        font-size: 12px;
        border: none;
        border-radius: 10px;
        box-sizing: border-box;
        outline: none;
        resize: none;
        background: #fff;
    }
</style>


