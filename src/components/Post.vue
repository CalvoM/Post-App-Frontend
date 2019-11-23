<template>
    <div id="Post">
        <p id="post-title">
            <span id="titleSpan">{{title}}</span>
            <span id="timeSpan">{{time}}</span> 
        </p>
       <p id="post-body">
           {{body}}
       </p>
       <button id="upvotes" @click="incrementPostVote">{{postUpvote}}</button>
       <button id="downvotes" @click="decrementPostVote">{{postDownvote}}</button>       
    </div>
</template>
<script>
import axios from 'axios';
import {cors_url,db_url} from '../config';
export default {
    name:"Post",
    props:{
        title:String,
        body:String,
        time:String,
        downvotes:Number,
        upvotes:Number,
        id:Number
    },
    data(){
        return{
            postUpvote:this.upvotes,
            postDownvote:this.downvotes
        }
    },
    methods:{
        incrementPostVote(){
            this.postUpvote++;
            axios.post(cors_url+db_url+'increment_upvote/',{id:this.id,increment_value:this.postUpvote})
        },
        decrementPostVote(){
            this.postDownvote++;
            axios.post(cors_url+db_url+'increment_downvote/',{id:this.id,increment_value:this.postUpvote})
        }
    }
}
</script>
<style lang="scss" scoped>
@import '../assets/fonts.css';
@import '../assets/colors.scss';
#Post{
    width:40%;
    background:lighten($primaryColor,20%); 
    padding: 0.2em 0;
    margin:0.5em auto;
}
#post-title,#post-body{
    border-bottom: 0.1px solid lighten($primaryTextColor,30%);
    padding-bottom: 0.5em;
}
#titleSpan{
    font-size: 110%;
    color:darken($primaryTextColor,30%);
    letter-spacing: 0.2em;
    font-family:Courgette;  
}
#timeSpan{
    font-size: 90%;
    margin-left:1em;
    color:#999;
}
#upvotes,#downvotes{
    border:none;
    padding:0.6em;
    margin:0.6em 0.5em;
    width: 3em;
}
#upvotes{
    background-color: #9f0;
}
#downvotes{
    background-color: rgb(247, 86, 17);
}
</style>