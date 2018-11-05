<template>
  <div id="msgs_search_div">
    <input type="search" v-bind:placeholder=inputPlaceholder  ></input>
    <hr/>
    <template v-for="contact in contacts">
      <div class="contact_div" v-on:click="selectContact">
        <img class="contact_text_img" v-bind:src=contact.picUrl />
        <div class="contact_text">
          <h3 class="contact_text_name">{{ contact.name }}</h3><p class="last_msg">{{ contact.msgs[contact.msgs.length - 1].text }}</p>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
  import {event_bus} from './main';

  export default{
    props:['contacts'],
    data(){
      return {
        inputPlaceholder:'Search'
      }
    },
    methods:{
      selectContact:function(event){
        let contactsArr = document.getElementsByClassName('contact_div');
        let i,curr_i;
        for(i=0;i<contactsArr.length;i++){
          contactsArr[i].classList.remove('select');
          if(contactsArr[i].innerHTML === event.currentTarget.innerHTML)
            curr_i = i;
        }
        event.currentTarget.classList.add('select');
        event_bus.$emit('select_contact', curr_i);

      }
    }
  }
</script>

<style scoped>
  #msgs_search_div{
    height:100%;
  }
  div{
    background-color:#444;
    float:left;
    width:18%;
  }
  .contact_div{
    vertical-align:middle;
    width:100%;
    height:70px;
    padding-top:4%;
  }
  .contact_div.select{
    background-color:#999;
  }
  .contact_div:hover{
    background-color:#777;
  }
  input{
    width:84%;
    height:3%;
    border:0px solid #eee;
    margin-top:10%;
    border-radius:1rem;
    background-color:#666;
    box-shadow:0;
    padding:15px;
    color:lightgray;
  }
  input::placeholder{
    color:lightgray;
  }
  input:focus{
    outline:none;
  }
  h3{
    margin-top:1%;
    color:#dedede;
    font-weight:bold;
    font-size:0.78vw;
    margin-left:3.5%;
    float:left;
    vertical-align:top;
    user-select:none;
    background-color:rgba(0,0,0,0);
  }
  hr{
    background-color:gray;
    margin-top:10%;
    margin-bottom:10%;
  }
  img{
    border-radius:50%;
    width:13%;
    float:left;
    margin-left:1.5%;
    user-select:none;
  }
  .last_msg{
    width:100%;
    height:40%;
    color:#cbcbcb;
    font-size:0.6vw;
    height:0.8vw;
    margin-left:3.5%;
    overflow:hidden;
    text-align:left;
    text-overflow:ellipsis;
    white-space:nowrap;
    user-select:none;
    background-color:rgba(0,0,0,0);
  }
  .contact_text{
    width:80%;
    cursor:pointer;
    background-color:rgba(0,0,0,0);
  }
</style>
