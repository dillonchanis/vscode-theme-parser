<template>
  <form @submit.prevent="submit">
    <div class='form-group'>
      <AppTextarea :value="json"
                   @input="onInput" />
      <p class="error"
         v-if="errorMessage">
        {{ errorMessage }}
      </p>
    </div>

    <div class='form-group'>
      <AppButton type="submit" primary>Submit</AppButton>
      <AppButton type="button"
                 @click.prevent="clear">
        Clear
      </AppButton>
    </div>
  </form>
</template>

<script>
import AppTextarea from "./Textarea";
import AppButton from "../Button";
import { isJSON } from "../../utils";

export default {
  name: "AppForm",
  components: {
    AppTextarea,
    AppButton
  },
  data: () => ({
    json: "",
    errorMessage: ""
  }),
  methods: {
    clear() {
      this.json = "";
      this.$emit("onClear");
    },
    onInput(text) {
      this.json = text;
      this.errorMessage = "";
    },
    submit() {
      if (!this.json) {
        this.errorMessage = "Paste theme JSON into the textarea.";
        return;
      }

      if (!isJSON(this.json)) {
        this.errorMessage = "Content must be valid JSON.";
        return;
      }

      this.$emit("onSubmit", this.json);
    }
  }
};
</script>

<style scoped>
.form-group {
  margin-bottom: 15px;
}

.error {
  color: #e64a45;
  font-size: 16px;
  font-style: italic;
  margin-top: 0.5em;
  margin-bottom: 0.5em;
}
</style>
