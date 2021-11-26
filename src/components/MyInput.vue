<template>
    <div>
        <el-input v-model="inputTodo"  @keyup.enter="enterFun" placeholder="请输入代办事项" clearable />
    </div>
</template>

<script>
import { ref, reactive, toRefs,  } from 'vue'

export default ({
    name:'MyInput',
    props:{
       addItem:Function, 
    },
    setup(props,ctx) {
        console.log('---setup----',props)

        const state = reactive({
            inputTodo:""
        })

        const enterFun =()=>{
            if(props.addItem){
                props.addItem(state.inputTodo)
            }
        }

        return{
            enterFun,
            ...toRefs(state)

        }
    },
})
</script>

<style scoped>
*{
    width: 300px;
    margin: 0 auto;
}
</style>


