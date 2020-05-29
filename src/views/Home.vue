<template>
  <div class="home">
    <b-container>
      <b-row class="d-flex justify-content-between">
        <div><input type="text" placeholder="search" v-model="cardSearch" class="cardSearchStyle"></div>
        <div><b-form-select v-model="sortType" :options="options" @change="onChangeSort"></b-form-select></div>
      </b-row>
      <b-row v-if="getPosts.length === 0">No Match Found</b-row>
      <b-row v-else>
        <Card v-for="(post,i) in getPosts" :key="i" :post="post"></Card>        
      </b-row>
    </b-container>  
    <ul>
      <li>vue 에서 uid 발생하는 메소드</li>
      <li>axios - 따로 api 폴더 만들기, firebase에 realdatabase에 등록해서 불러오기</li>
      <li>vuex</li>
      <li>1. router : 동적라우터 path/:id, Detail.vue 로 보내기</li>
      <li>transition</li>
      <li>search 된 부분이 hightlight 되도록 : udemy quasar</li>
    </ul>
  </div>
</template>

<script>
import Post from '@/data/post.js'
import Card from '@/components/Card'

export default {
  name: 'Home',
  data(){
    return {
      posts: Post,
      cardSearch:'',
      sortType: null,
      options: [
        { value: null, text: 'Please select sort type' },
        { value: '', text: 'Default' },
        { value: 'price', text: 'Price' },
      ],
    }
  },
  components: {
    Card
  },
  computed:{
    getPosts(){
      var filtered_posts = this.posts.filter((post) => {
        return post.title.toLowerCase().includes(this.cardSearch.toLowerCase())
      });
      
      if(this.sortType == 'price'){
        return filtered_posts.sort(function(a,b){
          return a.price - b.price
        });
      }else{
        return filtered_posts;
      }      
    }
  },
  methods:{
    onChangeSort(){      
      this.cardSearch = '';
    }
  },
  
}
</script>
