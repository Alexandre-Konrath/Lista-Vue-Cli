<template>

  <div class="form-todo form-group">
    <p>
      <input placeholder="Nome" type="text" name="author" class="form-control" v-model="name" />
    </p>
    <p>
      <textarea id="comentario" placeholder="Comentário" name="message" class="form-control"
        v-model="message"></textarea>
    </p>
    <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
  </div>

</template>

<script>
export default {
  data() {
    return {
      name: '',
      message: ''
    }
  },

  methods: {
    addComment() {
      if (this.message.trim() === '') {
        document.getElementById('comentario').focus()
        return
      }

      // agora preciso passar os valores que eu digito para os componentes de comentario.
      // com o metodo init ele dispara um evento e para todos que estao ouvindo ele vai capturar o valor que passa

      this.$emit('add-todo', {
        name: this.name,
        message: this.message
      })

      this.name = '';
      this.message = '';
    },
  }
}
</script>
