<template>
    <div id="Post">
        <p id="post-title">
            {{title}}
            {{time}}
        </p>
       <p id="post-body">
           {{body}}
       </p>
       <button id="upvotes">{{upvotes}}</button>
       <button id="upvotes">{{downvotes}}</button>       
    </div>
</template>
<script>
export default {
    name:"Post",
    props:{
        title:String,
        body:String,
        time:String,
        downvotes:Number,
        upvotes:Number
    }
}
</script>
<style lang="scss" scoped>
@import '../assets/fonts.css';
@import '../assets/colors.scss';
#Post{
    
}
</style>