<template>
    <div class="control_area">
        <select class="set_font" v-model="fontInfo.family" @change="reSetting" title="set font">
            <option value="" disabled>폰트를 선택해주세요.</option>
            <option v-for="fontOption in fontOptions" :key="fontOption.value" :name="fontOption.label">{{fontOption.label}}</option>
        </select>
        <select class="set_size" v-model="fontInfo.size" @change="reSetting" title="set size">
            <option v-for="sizeOption in sizeOptions" :key="sizeOption.value" :name="sizeOption.label">{{sizeOption.label}}</option>
        </select>
        <ul class="set_color">
            <li v-for="colorOption in colorOptions" :key="colorOption.value" @click="setColor(colorOption.value)" :style="{ background: colorOption.value }">
                {{colorOption.value}}
            </li>
        </ul>
    </div>
</template>

<script>
import EventBus from './EventBus.vue';
export default {
    data() {
        return {
            fontInfo: {
                family: '',
                size: '12px',
                color: '#666'
            },
            fontOptions: [
                { label: 'makdae', value: 'makdae' },
                { label: 'yanolza', value: 'yanolza' },
                { label: 'serif', value: 'serif' },
                { label: 'san-serif', value: 'san-serif' },
                { label: 'cursive', value: 'cursive' }
            ],
            sizeOptions: [
                { label: '12px', value: '12' },
                { label: '24px', value: '24' },
                { label: '36px', value: '36' }
            ],
            colorOptions: [
                { label: 'black', value: '#666' },
                { label: 'red', value: '#fc5a5a' },
                { label: 'green', value: '#a9d657' },
                { label: 'blue', value: '#8cbdff' }
            ]
        }
    },
    methods: {
        reSetting() {
            EventBus.$emit('sendInfo', this.fontInfo);
        },
        setColor(color) {
            this.fontInfo.color = color;
            this.reSetting();
        }
    }
}
</script>

<style lang="scss" scoped>
    .control_area {
        width: 100%;
        margin-bottom: 15px;
        font-size: 12px;
        overflow: hidden;
    }
    select {
        height: 35px;
        margin-right: 10px;
        color: #777;
        border: 1px solid #ddd;
        border-radius: 5px;
        outline: none;
        &.set_font {
            width: 50%;
        }
        &.set_size {
            width: 15%;
        }
    }
    .set_color {
        display: inline-block;
        margin-left: 10px;
        li {
            display: inline-block;
            width: 15px;
            height: 15px;
            margin-right: 10px;
            border-radius: 50px;
            text-indent: -99999px;
            cursor: pointer;
        }
    }
</style>

