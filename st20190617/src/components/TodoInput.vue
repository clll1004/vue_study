<template>
    <div class="input_area shadow">
        <label for="todoInpue"></label>
        <input type="text" id="todoInpue" v-model="newItem" @keyup="showClearInputBox" @keyup.enter="passItem" class="input_box" placeholder="할 일을 입력하세요!" autofocus/>
        <button class="add_btn" @click="passItem"><i class="fa fa-plus"></i></button>
        <i class="clear_input fa fa-times" v-if="showClearInput" @click="clearInputBox"></i>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newItem: '',
            showClearInput: false
        }
    },
    methods: {
        passItem() {
            if (this.newItem !== '') {
                this.$emit('passItem', this.newItem);
                this.newItem = '';
                this.showClearInput = false;
            } else {
                alert('할 일을 입력해주세요!');
            }
        },
        showClearInputBox() {
            this.showClearInput = this.newItem !== '';
        },
        clearInputBox() {
            this.newItem = '';
            this.showClearInput = false;
        }
    }
}
</script>

<style scoped>
    .input_area {
        width: 100%;
        height: 50px;
        margin-bottom: 30px;
        background: rgba(0,0,0,.2);
        border-radius: 5px;
        overflow: hidden;
    }
    .input_box {
        float: left;
        width: 65%;
        height: 50px;
        padding-left: 15px;
        line-height: 50px;
        background: rgba(0,0,0,0);
        color: #fff;
        border: none;
        outline: none;
    }
    .input_box::placeholder {color: #eee;}
    .clear_input {
        float: right;
        width: 2rem;
        height: 50px;
        line-height: 50px;
        color: #ddd;
        cursor: pointer;
    }
    .add_btn {
        float: right;
        width: 3rem;
        height: 50px;
        line-height: 50px;
        color: #f1f7e6;
        background: rgba(0,0,0,0);
        outline: none;
        border: none;
        border-radius: 0 5px 5px 0;
        cursor: pointer;
    }
</style>
