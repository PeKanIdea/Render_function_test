<script>
export default {
  render: function(createElement) {
    var self = this;
    return createElement("input", {
      on: {
        keyup: function(event) {
          if (event.keyCode !== 13) return;
          self.$emit("inputToDo", event.target.value);
          event.target.value = "";
        }
      },
      style: {
        width: "100%",
        padding: "8px 10px",
        border: "4px solid red"
      }
    });
  }
};
</script>

