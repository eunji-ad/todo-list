<template>
    <div class="input">
        <input 
        class="input_txt"
        type="text"
        v-model="newTodoItem"
        placeholder="To do list"
        v-on:keypress.enter="addTodo"
        >
        <!-- v-model: 입력필드 데이터를 뷰 데이터 속성에 연결 -->
        <!-- @keyup.enter: enter키 감지하여 함수 호출 / @click: 클릭 감지 -->
        <!-- newTodoItem: 필드 작성된 텍스트를 담는 변수 -->
        <button 
        class="input_btn"
        v-on:click="addTodo"
        >
            <i class="far fa-plus input_btn_ic" aria-hidden="true"></i>
        </button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ""        };
    },

    methods: {
        addTodo() {
            if (this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit("addTodo", value);
                this.clearInput(); //clearInput 함수처리
            } else {
                alert(" 새로운 목록을 추가해주세요 ")
            }
        },
        clearInput() {
            this.newTodoItem = "";
        }
    },
};
</script>

<style lang="scss" scoped>
    .input {
        margin-bottom:30px;

        border-radius:18px;
        width:100%;
        padding:5px;
        box-shadow:inset 4px 4px 12px rgba(0,0,0,0.1);

        &_txt {
            outline:none;
            border-radius:12px;
            padding:15px 25px;
            width:calc(100% - 50px);
            font-size:18px;
        }

        &_btn {
            width: 46px;height:46px;
            border-radius:13px;
            box-shadow:2px 2px 10px rgba(0,0,0,0.25);
            line-height:52px;
            background:#f9f9f9;
            cursor:pointer;

            &_ic {
                color:#999;
                font-size:25px;
            }
        }
    }
</style>