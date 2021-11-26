<template>
  <div class="home">
    <MyInput ref='myInputRef' :addItem="addTodo"/>
    <MyList :tableDate="todolist" />
  </div>
</template>

<script>
// @ is an alias to /src
import MyInput from "@/components/MyInput.vue";
import MyList from "@/components/MyList.vue";
import { reactive, toRefs, ref } from "vue";

export default {
  name: "Home",
  components: {
    MyInput,
    MyList,
  },
  setup() {
    //这是一个数据管理
    const state = reactive({
      todolist: [
        { todo: "吃饭", checkFlag: false },
      ],
    });
    //vue3.0中调用子组件中方法需要这样写
    const myInputRef = ref(null)

    const addTodo = (id)=>{
      state.todolist.push({ todo: id, checkFlag: false },)
      myInputRef.value.inputTodo = '';
    }

    return {
      myInputRef,
      addTodo,
      ...toRefs(state),
    };
  },
};
</script>
