<template>
  <div class="home">
    <PostModal v-show="showPostModal" @closePostModal="closeModal"></PostModal>
    <NavBar @addPost="showPostModal=!showPostModal"></NavBar>
    <Loading v-if="!posts.length"></Loading>
    <Post v-else v-for="(post,index) in posts.reverse()" :key="index" :title="post.title" :body="post.body" :time="customizeTime(post.posted_at)" :upvotes="post.upvotes" :downvotes="post.downvotes" :id="post.id"> {{post}} </Post>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar";
import PostModal from "@/components/PostModal";
import Loading from "@/components/Loading";
import Post from '@/components/Post';
import axios from 'axios';
import {cors_url,db_url} from '../config';
export default {
  name: 'home',
  components:{
    NavBar,
    PostModal,
    Loading,
    Post
  },
  data(){
    return{
      showPostModal:false,
      Post:{
        title:"",
        body:""
      },
      posts:[],
    }
  },
  methods:{
    closeModal(){
      this.showPostModal =! this.showPostModal;
    },
    customizeTime(posted_at){
      const minute_mark = 60000;
      const hour_mark = 60 * minute_mark;
      const day_mark = 24*hour_mark;
      let now = new Date()
      let post_time = new Date(posted_at)
      let time_difference = now - post_time;
      if(time_difference > day_mark){
        return (time_difference/day_mark).toFixed(0).toString()+"d";
      }
      else if(time_difference > hour_mark){
        return(time_difference/hour_mark).toFixed(0).toString()+"h";
      }
      else if(time_difference > minute_mark){
        return(time_difference/minute_mark).toFixed(0).toString()+"m";
      }
      else{
        return(time_difference/1000).toFixed(0).toString()+"s";
      }
    }
  },
  created(){
    axios.get(cors_url+db_url+'get/posts/')
          .then(resp =>{
            let posts_array = resp.data.posts;
            posts_array.forEach(element =>{
              this.posts.push(element);
            }) 
          })
  }
}
</script>
<style lang="scss" scoped>

</style>