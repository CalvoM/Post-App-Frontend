<template>
  <div class="home">
    <PostModal></PostModal>
    <NavBar></NavBar>
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
  }
}
</script>
<style lang="scss" scoped>

</style>