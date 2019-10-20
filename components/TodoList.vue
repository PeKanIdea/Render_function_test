<script>
import BaseInputText from "./BaseInputText.vue";
import TodoListItem from "./TodoListItem.vue";

let nextTodoId = 1;

export default {
  data() {
    return {
      todos: [
        {
          id: nextTodoId++,
          text: "Lorem ipsum dolor"
        },
        {
          id: nextTodoId++,
          text: "sit amet, consectetur"
        },
        {
          id: nextTodoId++,
          text: "adipiscing elit, sed do"
        }
      ]
    };
  },

  methods: {
    addTodo(value) {
      if (value) {
        this.todos.push({
          id: nextTodoId++,
          text: value
        });
      }
    },
    removeTodo(idToRemove) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== idToRemove;
      });
    },
    renderOption(createElement) {
      let self = this;

      if (this.todos.length) {
        return createElement("ul", [
          this.todos.map(function(item) {
            return createElement(TodoListItem, {
              props: {
                todo: item
              },
              on: {
                remove: function(id) {
                  self.removeTodo(id);
                }
              }
            });
          })
        ]);
      } else {
        return createElement("p", "Ничего не найдено.");
      }
    }
  },

  render: function(createElement) {
    let self = this;

    return createElement("div", {}, [
      createElement(BaseInputText, {
        attrs: {
          placeholder: "New ToDo"
        },
        on: {
          inputToDo: function(value) {
            self.addTodo(value);
          }
        }
      }),
      this.renderOption(createElement)
    ]);
  }
};
</script>