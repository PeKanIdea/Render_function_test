<script>
export default {
render: function (createElement) {
    let self = this
    return createElement(
      'li',
      [
        this.todo.text,
        createElement('button',{
          on: {
            click: function () {
              self.$emit('remove', self.todo.id)
            } 
          }
        },['X'])
      ]
    )
  },
    props: {
      todo: {
        type: Object,
        required: true
      }
    }
}
</script>


