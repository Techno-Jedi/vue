<template>
  <div>
    <form @submit.prevent class="form">
      <h2>Созданиие поста</h2>
      <my-input
          v-model="post.title"
          type="text"
          placeholder="Название"
      />
      <my-input
          v-model="post.body"
          type="text"
          placeholder="Описание"
      />
      <my-button
          @click="createPost"
      >
        Добавить пост</my-button>
    </form>
  </div>
</template>

<script>

export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }
  }
}
</script>

<style scoped>

.form{
  display: flex;
  flex-direction: column;
}
</style>