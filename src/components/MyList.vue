<template>
  <div v-for="item in tableDate" :key="item.todo">
    <el-checkbox v-model="item.checkFlag"> {{ item.todo }} </el-checkbox>
  </div>
</template>

<script>
import { ref, reactive, toRefs, watch } from "vue";

export default {
  name: "MyList",
  props: {
    tableDate: Array,
  },
  setup(props, ctx) {
    console.log("---setup----", props);

    watch(props.tableData, (_, newer) => {
      state.tableData = newer;
    });

    return {};
  },
};
</script>
