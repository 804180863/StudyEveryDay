<template>
    <div>
        <div :v-text="eg"></div>
    </div>
</template>
<script>
import xxx from 'xxx' //引入文件或者组件
    export default {
        data() {
            return {
                eg:'i love vue'
            };
        },
        //页面方法的钩子
        methods: {
            egg(){
                console.log('eg')
            }
        },
        //初始创建前触发的钩子
        created() {
            this.egg()
        },
        //渲染DOM时触发的钩子
        mounted(){
             this.egg()
        },
        //页面更新后触发的钩子
        updated() {
             this.egg()
        },
        //页面销毁触发的钩子
        destroyed(){
             this.egg()
        }
       
    };
</script>
// 这个scoped 写上了只在当前页面生效 不写可能子组件中也会生效
<style scoped>
</style>