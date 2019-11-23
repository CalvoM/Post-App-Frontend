<template>
    <div id="post-modal">
        <div id="postContainer">
        <div id="titleSection">
            <input type="text" placeholder="Enter the title" id="title" v-model="Post.title">
            <button id="closeBtn" @click="$emit('closePostModal')">x</button>
        </div>
        <div id="bodySection">
            <textarea name="body" id="body" cols="30" rows="10" placeholder="Enter body of your post" v-model="Post.body"></textarea>
        </div>
        <div id="submitSection">
            <button id="submitBtn" @click="addPostToDb">SUBMIT POST</button>
        </div>
        </div>
    </div>
</template>
<script>
import {cors_url,db_url} from "../config";
import axios from 'axios';
export default {
    name:"post-modal",
    data(){
        return{
            Post:{
                title:"",
                body:""
            }
        }
    },
    methods:{
        addPostToDb(){
            axios.post(cors_url+db_url+'add/posts/',this.Post)
                 .then(resp =>{
                     console.log(resp)
                     this.Post.title = "";
                     this.Post.body="";
                 })
        }
    }
}
</script>
<style lang="scss" scoped>
@import '../assets/colors.scss';
#post-modal{
    z-index:100;
    position: fixed;
    background-color: rgba(darken($primaryColor,40%),0.4);
    width:100%;
    height:100%;
}
#postContainer{
    padding: 0.9em;
    width:40%;
    margin:auto;
    margin-top: 5em;
    background-color: rgba(darken($primaryColor,15%),0.4);

}
#titleSection{
    padding:0.5em;
    // border-bottom: 1px solid $primaryColor;
    text-align: left;
}
input,textarea,button{
    background-color: transparent;
    outline:none;
    border-radius: 0;
}
#titleSection > input{
    border:1px solid $primaryColor;
    width:60%;
    padding:0.5em;
    color:darken($primaryTextColor,16%);
}
#closeBtn{
    border:1px solid $primaryColor;
    padding:0.5em;
    margin-left:20%;
    width:40px;
    height:40px;
    color:$primaryTextColor;
    border-radius: 50%;
}

#bodySection{
    padding:0.3em;
}
#body{
    margin-top: 0.5em;
    width:96%;
    padding:0.5em;
    margin:auto;
    border:1px solid $primaryColor;
    font-size: 110%;
    color:darken($primaryTextColor,16%);
    resize: none;
}

#submitBtn{
    margin:0.5em auto;
    padding:0.5em;
    border:1px solid $primaryColor;
    color:$primaryTextColor;
}
#body:focus,#title:focus,#closeBtn:focus,#submitBtn:focus{
    box-shadow: 1px 1px 4px 2px $primaryColor;
}
</style>