<template>
    <div id="Navbar">
        <header id="title">Post it!</header>
        <input type="text" placeholder="Search for posts" id="searchInput">
        <button id="addPostBtn" @click="$emit('addPost')">Add a post</button>
    </div>
</template>

<script>
export default {
    name:'NavBar',
}
</script>

<style lang="scss" scoped>
@import '../assets/colors.scss';
@import '../assets/fonts.css';
#Navbar{
   background-color:$primaryColor;
   width:100%;
   padding:0.8em;
   text-align:left;
}
#title{
    font-family: Courgette;
    letter-spacing: 0.3em;
    font-size:110%;
    display: inline;
    color:$primaryTextColor;
   margin-left:1%;
    font-weight:bold;
}
#searchInput{
    border-radius: 0;
    border:none;
    padding:0.5em;
    margin-left:20%;
    width:25%;
}
#addPostBtn{
    border:none;
    padding:0.5em;
    margin-left:15%;
    background-color: lighten($primaryTextColor,19%);
    color:darken($primaryColor,20%);
    font-family: Courgette;
    letter-spacing: 0.3em;
}
</style>