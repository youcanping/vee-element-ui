<template>
  <div id="app">
    <!-- <EForm /> -->
    <RefactoredForm />
  </div>
</template>

<script>
import EForm from "./components/Form";
import RefactoredForm from "./components/RefactoredForm";

export default {
  name: "App",
  components: {
    // EForm,
    RefactoredForm,
  },
};
</script>

