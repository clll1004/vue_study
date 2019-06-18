<template>
    <div>
        <ul v-if="!showEmpty">
            <li class="shadow" v-for="(todoItem, index) in propsItems" :key="todoItem">
                <i class="check_icon fa fa-check-square"></i>
                {{todoItem}} 
                <button class="remove_btn" @click="removeItem(todoItem, index)"><i class="fa fa-minus"></i></button>
            </li>
        </ul>
        <div class="empty" v-if="showEmpty">
            리스트가 없습니다.
        </div>
    </div>
</template>

<script>
export default {
    props: ['propsItems', 'showEmpty'],
    methods: {
        removeItem(todoItem, index) {
            localStorage.removeItem(todoItem);
            this.propsItems.splice(index, 1);
            if (!this.propsItems.length) {
                this.passClear();
            }
        },
        passClear() {
            this.$emit('passClear');
        }
    }
}
</script>

<style scoped>
    ul {
        width: 100%;
        list-style: none;
    }
    li {
        position: relative;
        height: 45px;
        line-height: 45px;
        padding: 0 15px;
        margin-bottom: 10px;
        border-radius: 5px;
        font-size: 0.9rem;
        text-align: left;
        color: #777;
        background: #fff;
        word-break: break-all;
        overflow: hidden;
    }
    .check_icon {
        margin-right: 5px;
        color: #d0e2ae;
    }
    .remove_btn {
        position: absolute;
        right: 15px; top: 16px;
        border:none; 
        background: none;
        cursor: pointer;
        outline: none;
    }
    .remove_btn i {
        color: #ff2828;
    }
    .empty {
        padding: 15px 0;
        color: #eee;
        font-size: 0.9rem;
    }
</style>
