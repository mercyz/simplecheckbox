<template>
  <div class="container">
      <div class="card"  @click="checkbox($event)" v-for="(username, index) in codepally" :key="index">
        <input class="checkbox" type="checkbox" :value="username[0]"  v-model="selected"> 
        <label class="username" for="{username[0]}">{{username[1]}}</label>
      </div>
      <p class="flex">{{selected.join(",")}}</p>
  </div>
</template>
<script>
import { codepally_data } from "../lib/app.js";
export default {
      name: "Hello",
      data: () => ({
          selected: [],
          codepally: [],
      }),
      mounted: function(){
         let c = Object.keys(codepally_data).map((key) => [key, codepally_data[key]]);
          this.codepally = c
      },
      methods: {
         checkbox(event){
            if(event.target.tagName == "LABEL"){
              event.target.parentNode.classList.toggle("blue")
            }
            if(event.target.type == "checkbox"){
              event.target.parentNode.classList.toggle("blue")
            }
              event.target.classList.toggle("blue")
        },
      }
}
</script>
<style>
  .container{
      width: 300px;
      display: flex;
      flex-direction: column;
  }
  .card{
    margin-bottom: 5px;
    display: flex;
    box-shadow: 0px 1px 4px #eee;
    padding: 0px 9px;
    width: 240px;
    background:white;
    cursor: pointer;
    }
    .username{
      padding:10px 3px;
      margin:0;
    }
    .checkbox{
      outline: none;
    }
    .blue{
      background:dodgerblue;
      color:white
    }
    .flex{
      display: flex;
    }
  </style>