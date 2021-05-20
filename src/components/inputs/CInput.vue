<template>
  <el-input v-model="value" @blur="$emit('blur', $event)"></el-input>
</template>
<script>
export default {
  data() {
    return {
      value: "",
    };
  },
  mounted() {
    console.log(this);
    setTimeout(() => {
      this.$emit("change");
    }, 2000);
  },
};
</script>