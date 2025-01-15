<template>
    <div class="list">
        <transition-group class="list_wrap" name="list" tag="ul">
          <li 
            class="list_li"
            v-for="(todoItem, idx) in propsdata"
            v-bind:key="todoItem"
            >
                <input 
                type="checkbox"
                class="ch"
                >
                <span class="list_cont">{{todoItem}}</span>
                <i 
                class="list_delete"
                v-on:click="removeTodo(todoItem, idx)"
                >
                    <i class="far fa-trash"></i>
                </i>
            </li>
        </transition-group>
    </div>
</template>
  

<script>
export default {
    props: ["propsdata"],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit("removeTodo", todoItem, index);
        },
    },
};
</script>

<style lang="scss" scoped>
    .list{
        padding:15px 10px;
        border-radius:18px;
        box-shadow:inset 5px 4px 12px rgba(0,0,0,0.15);
        height:450px;
        overflow-y:auto;
 
       &_li {
        background: #fff;
        display: flex;
        align-items: center;
        justify-content: space-between;
        border: 1px solid #fff;
        padding: 20px 20px;
        margin-bottom: 10px;
        border-radius: 18px;
        box-shadow: 2px 2px 12px rgba(0, 0, 0, 0.25);

        input {
            margin-right:10px;
            outline:none;
            border:none;
            &:checked {
                accent-color:#EC5D57;
            }
        }

        input:checked + span {
            text-decoration:line-through;
            opacity:0.4;
        }

        input:checked + li {opacity:0.6;}

        .list_cont:has(.ch:checked) {
            opacity:0.3;
        }

        span {
            width:70%;
            word-break:break-word;
            text-align:left;
        }

        .list_delete {
            margin-left:8px;
            transition:0.3s;
            color:#EC5D57;
            border-radius:50%;
            padding:6px 10px;

            &:hover {
                transform:scale(1.2);
                background:rgba(255,0,0,0.2);
                color:rgba(255,0,0,0.7);
            }
        }
       }
    }
    // transition-group css 활용 명명
    .list-enter-active,
    .list-leave-active {
        transition: all 1s;
    }
    .list-enter,
    .list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }
    // 
</style>