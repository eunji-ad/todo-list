<template>
    <div class="footer">
        <button 
        class="footer_btn"
        v-on:click="clearTodo"
        >
            <i class="far fa-trash"></i>
            Delete All
        </button>
    </div>    
</template>

<script>
export default {
    methods: {
        clearTodo() {
            this.$emit("removeAll");
        },
    },
}
</script>

<style lang="scss" scoped>
    .footer {
        margin:25px auto 0;
        text-align:right;

        &_btn {
            border:none;outline:none;
            border-radius:12px;
            width:45%;text-align:center;
            height:42px;line-height:40px;
            background:rgba(255, 0, 0, 0.3);
            color:#fefefe;font-size:14px;
            transition:0.3s;
            cursor:pointer;

            i {margin-right:6px;}

            &:hover {
            background:rgba(255, 0, 0, 1);  
            color:#fff;              
            }
        }
    }
</style>