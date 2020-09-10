<template>
 <li>
                <slot name="pre-slot" :value="value"></slot>
                <span v-if="!del">{{title}}</span>
                <span class="red" v-else style="text-decoration: line-through;">{{title}}</span>
                <slot name="suf-slot">😄</slot>
                <slot name="default-slot">😄</slot>
                <button v-show="!del" @click="handleClick">删除</button>
            </li>
  
</template>

<script>
export default {
            props: {
                title: String,
                del: {
                    type: Boolean,
                    default: false
                }
            },
            //data值为函数，不能为对象，因为对象为引用数据类型。导致可以容易篡改
            data: function () {
                return {
                    value:Math.random()
                }
            },
            methods: {
                handleClick(){
                    console.log('点击删除！');
                    //click事件通过emit从子组件向父组件传递相关参数
                    this.$emit('delete',this.title);
                }
            }
}
</script>

<style scoped>
.red{
    color: red;
}

</style>
