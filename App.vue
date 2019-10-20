<script>
import TodoList from "./components/TodoList.vue";

export default {
  render: function(createElement) {
    return createElement(
      "div",
      {
        attrs: {
          id: "app"
        },
        style: {
          maxWidth: "400px",
          margin: "0 auto",
          lineHeight: "1.4",
          fontFamily: '"Avenir", Helvetica, Arial, sans-serif',
          color: "red"
        }
      },
      [
        createElement(
          "h1",
          {
            style: {
              textAlign: "center"
            }
          },
          ["My To Do App"]
        ),
        createElement(TodoList)
      ]
    );
  }
};
</script>


