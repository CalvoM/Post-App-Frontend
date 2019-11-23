<template>
    <div id="Loading">
        No posts
        <button id="reloadBtn" @click="reloadPage">RELOAD</button>
    </div>
</template>
<script>
export default {
    name:"Loading",
    methods:{
        reloadPage:function(){
            location.reload();
        }
    }
}
</script>
<style lang="scss" scoped>
@import '../assets/fonts.css';
@import '../assets/colors.scss';
#Loading{
    font-family: Courgette;
    letter-spacing: 0.3em;
}
#reloadBtn{
    display: block;
    margin:1em auto;
    padding:0.5em;
    border-radius: 0;
    border:none;
    background-color: $primaryColor;
    color:$primaryTextColor;
    font-family: Courgette;
    letter-spacing: 0.5em;
}
</style>