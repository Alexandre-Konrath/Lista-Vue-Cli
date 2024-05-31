<template>

  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <!--! capitura eventos  -->
    <FormTodo v-on:add-todo='addComment'></FormTodo>
    <div class="list-group mt-3">
      <p v-if="comments.length <= 0">Sem Comentarios...</p>
      <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
        <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
        <p>{{ comment.message }}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
        </div>
      </div>
    </div>
    <hr />
  </div>

</template>

<script>
// import do componente
import FormTodo from './FormTodo.vue';
// quando eu exporto este objeto é a mesma coisa que eu estar dando um newVue
export default {
  name: 'UserComments',
  components: {
    FormTodo
  },

  data() {
    return {
      comments: []
    }
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment)
    },

    removeComment(index) {
      this.comments.splice(index, 1);
    }
  },

  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === '' ? 'Anônimo' : comment.name
      }))
    }
  },

  watch: {
    comments(val) {
      console.log('val', val)
    }
  }
}
</script>

<style></style>
