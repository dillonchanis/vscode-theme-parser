<script>
export default {
  name: "AppButton",
  functional: true,
  props: {
    primary: {
      type: Boolean,
      default: false
    }
  },
  render(h, { props, slots, data }) {
    if (props.primary) {
      return h(
        "button",
        { ...data, class: "btn btn-primary" },
        slots().default
      );
    }

    return h("button", { ...data, class: "btn" }, slots().default);
  }
};
</script>

<style scoped>
.btn {
  display: inline-block;
  height: 40px;
  background-color: transparent;
  margin-right: 10px;
  color: #3c424f;
  padding: 0 32px;
  border: none;
  border-radius: 4px;
  font-size: 15px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.025em;
  cursor: pointer;
}

.btn-primary {
  background-color: #e8308c;
  color: #fff;
  box-shadow: 0 4px 6px rgba(50, 50, 93, 0.11), 0 1px 3px rgba(0, 0, 0, 0.08);
  opacity: 1;
  transition: background-color 0.25s ease, opacity 0.25s ease,
    transform 0.25s ease;
}

.btn-primary:hover {
  background-color: #e8308c;
  opacity: 0.8;
  transform: translateY(-1px);
  box-shadow: 0 7px 14px rgba(50, 50, 93, 0.1), 0 3px 6px rgba(0, 0, 0, 0.08);
}
</style>
