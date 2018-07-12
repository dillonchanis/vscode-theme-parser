<template>
  <textarea class='textarea'
            placeholder='Paste JSON here...'
            :value="value"
            v-on="listeners"></textarea>
</template>

<script>
export default {
  name: "AppTextarea",
  props: {
    value: {
      type: [String, Number],
      default: ""
    }
  },
  computed: {
    listeners() {
      return {
        ...this.$listeners,
        input: event => this.$emit("input", event.target.value)
      };
    }
  }
};
</script>

<style scoped>
.textarea {
  width: 90%;
  font-family: "Lora", serif;
  font-size: 16px;
  height: 80px;
  color: #3c424f;
  background-color: #efefef;
  padding: 10px;
  border: none;
  border-radius: 4px;
  resize: vertical;
  appearance: none;
}

@media screen and (min-width: 1080px) {
  .textarea {
    width: 75%;
    height: 150px;
  }
}
</style>
