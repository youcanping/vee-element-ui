<template>
  <ValidationObserver ref="observer" v-slot="{ handleSubmit }">
    <el-form ref="form" label-width="120px">
      <InputWithValidation
        v-model="email"
        rules="required|email"
        label="Email"
      />

      <InputWithValidation
        v-model="password"
        type="password"
        rules="required"
        label="Password"
        vid="password"
      />

      <InputWithValidation
        v-model="confirmation"
        type="password"
        rules="required|confirmed:password"
        label="Password confirmation"
      />

      <CustomWithValidation type="input" rules="required" label="custom" />

      <SelectWithValidation rules="required" label="Subject" v-model="subject">
        <el-option label="None" value></el-option>
        <el-option label="Subject 1" value="s1"></el-option>
        <el-option label="Subject 2" value="s2"></el-option>
      </SelectWithValidation>

      <CheckboxesWithValidation
        rules="required|length:2"
        name="Drinks"
        v-model="choices"
      >
        <el-checkbox label="Coffee"></el-checkbox>
        <el-checkbox label="Tea"></el-checkbox>
        <el-checkbox label="Soda"></el-checkbox>
      </CheckboxesWithValidation>

      <el-form-item>
        <el-button type="primary" @click="handleSubmit(onSubmit)"
          >Create</el-button
        >
        <el-button @click="resetForm">Reset</el-button>
      </el-form-item>
    </el-form>
  </ValidationObserver>
</template>

<script>
import { ValidationObserver } from "vee-validate";
import InputWithValidation from "./inputs/InputWithValidation";
import CustomWithValidation from "./inputs/CustomWithValidation";
import SelectWithValidation from "./inputs/SelectWithValidation";
import CheckboxesWithValidation from "./inputs/CheckboxesWithValidation";

export default {
  name: "EForm",
  components: {
    ValidationObserver,
    InputWithValidation,
    CustomWithValidation,
    SelectWithValidation,
    CheckboxesWithValidation,
  },
  data: () => ({
    email: "",
    password: "",
    confirmation: "",
    subject: "",
    choices: [],
  }),
  methods: {
    onSubmit() {
      console.log("Form submitted yay!");
    },
    resetForm() {
      this.email = "";
      this.password = "";
      this.confirmation = "";
      this.subject = "";
      this.choices = [];
      requestAnimationFrame(() => {
        this.$refs.observer.reset();
      });
    },
  },
  mounted() {
    console.log(this.$refs);
  },
};
</script>
