<template>
  <ValidationProvider
    :vid="vid"
    :name="$attrs.label"
    :rules="rules"
    v-slot="{ validate, errors }"
    slim
  >
    <el-form-item :error="errors[0]" :label="$attrs.label">
      <c-input @change="validate" />
    </el-form-item>
  </ValidationProvider>
</template>

<script>
import { ValidationProvider } from "vee-validate";
import CInput from "./CInput.vue";
export default {
  components: {
    ValidationProvider,
    CInput,
  },
  props: {
    vid: {
      type: String,
    },
    rules: {
      type: [Object, String],
      default: "",
    },
    // must be included in props
    value: {
      type: null,
    },
  },
  data: () => ({
    innerValue: "",
  }),
  watch: {
    // Handles internal model changes.
    innerValue(newVal) {
      this.$emit("input", newVal);
    },
    // Handles external model changes.
    value(newVal) {
      this.innerValue = newVal;
    },
  },
  created() {
    if (this.value) {
      this.innerValue = this.value;
    }
  },
};
</script>
