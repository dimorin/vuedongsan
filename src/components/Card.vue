<template>
  <div>
      <b-card
        :title="post.title"
        :sub-title="post.caption"
        :img-src="post.image"
        :img-alt="post.image"
        img-top
        tag="article"
        style="max-width: 20rem;"
        class="mb-2"
      >
        <b-card-text>{{post.price}}</b-card-text>

        <b-button href="#" variant="primary" @click="onView">view</b-button>
      </b-card>
  </div>
</template>

<script>
export default {
  props:{
    post:Object,
  },
  methods:{
      onView(){
          console.log(this.post.id)
      }
  }
}
</script>

<style>

</style>