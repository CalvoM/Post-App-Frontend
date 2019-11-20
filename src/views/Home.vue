<template>
  <div class="home">
    <PostModal v-show="showPostModal" @closePostModal="closeModal"></PostModal>
    <NavBar @addPost="showPostModal=!showPostModal"></NavBar>
  </div>
</template>

<script>
import NavBar from "@/components/NavBar";
import PostModal from "@/components/PostModal";
export default {
  name: 'home',
  components:{
    NavBar,
    PostModal,
  },
  data(){
    return{
      showPostModal:false,
      Post:{
        title:"",
        body:""
      }
    }
  },
  methods:{
    closeModal(){

    }
  }
}
</script>
<style lang="scss" scoped>

</style>