<template>
  <div id="msg_panel_div">
      <div id="top_bar">
        <h4 id="contact_name">{{ contacts[0].name }}</h4>
        <div id="" class="contact_options"><img v-bind:src=pathToAssets+favImg /></div>
        <div id="" class="contact_options"><img v-bind:src=pathToAssets+phoneImg /></div>
        <div id="" class="contact_options"><img v-bind:src=pathToAssets+camImg /></div>
      </div>
      <hr />
      <div id="messages">
        <div class="msg_container">
          <span class="msg received_msg">{{contacts[0].msgs[contacts[0].msgs.length - 1].text}}</span>
        </div>
      </div>
      <div id="bottom_bar">
        <button id="attach_btn"><img id="attach_img" v-bind:src=pathToAssets+attachImg /></button>
        <input type="text" id="msg_input" v-bind:placeholder=msgPlaceholder></input>
        <span id="emoji"></span>
        <button id="send_msg" v-on:click="sendMsg"><img id="send_img" v-bind:src=pathToAssets+sendImg /></button>
      </div>
  </div>
</template>
<script>
  import {event_bus} from './main';

  export default{
    props:['contacts'],
    data(){
      return {
          msgPlaceholder:'Type your message..',
          pathToAssets:'./src/assets/',
          sendImg:'send-btn.png',
          attachImg:'attach-btn.png',
          favImg:'fav-btn.png',
          camImg:'cam-btn.png',
          phoneImg:'phone-btn.png',
          msgElement:'<div></div>',
          currContactIndex:0
      }
    },
    methods:{
      sendMsg: function(event){
        let val = document.getElementById('msg_input').value;
        let newMsg = '<div class="msg_container" ><span class="msg sent_msg">' + val + '</span></div>';
        let messages = document.getElementById('messages');
        messages.innerHTML += newMsg;
        document.getElementById('msg_input').value = "";
        this.contacts[this.currContactIndex].msgs.push({text:val,type:'sent'});

      }
    },
    created(){
      event_bus.$on('select_contact', (data) => {
        //alert("this is the message panel. Data received: " + data);
        this.currContactIndex = data;
        let msg_cont = document.getElementById('messages');
        msg_cont.innerHTML = "";
        let new_content = '';
        let contacts_var = this.contacts;
        contacts_var[data].msgs.forEach(function(val){
          new_content += '<div class="msg_container"><span class="msg ' + val.type + '_msg">'+ val.text +'</span></div>';
        });
        msg_cont.innerHTML = new_content;
      });
    }
  }
</script>

<style scoped>
  #messages{
    overflow-y:auto;
  }
  #msg_panel_div{
    width:48%;
    background:rgb(234,238,242);
    float:left;
    height:100%;
  }
  #msg_input{
    background:rgb(251,252,252);
    border:0px solid #333;
    width:50%;
    height:80%;
    margin-top:6px;
  }
  input:focus, button:focus{
    outline:none;
  }
  #trashcan{
    width:10%;
    background:
  }
  button{
    border:none;
    background-color:rgba(0,0,0,0);
    cursor:pointer;

    margin-top:10px;
  }
  #send_msg{
    float:right;
    margin-right:20px;
  }
  #attach_btn{
    float:left;
    margin-left:30px;
  }
  img{
    border-radius:50%;
    background-color:white;
    width:35px !important;
    height:35px !important;

  }
  .contact_options{
    width:12%;
    height:100%;
    border-left:1px solid lightgray;
    float:left;
    vertical-align:middle;
  }
  .contact_options>img{
    margin-top:13px;
  }
  hr{
    margin-top:0;
  }
  #contact_name{
    width:64%;
    height:100%;
    display:inline-block;
    text-align:left;
    float:left;
    padding-left:40px;
    padding-top:20px;
  }
  #top_bar{
    height:8%;
  }
  #messages{
    height:84%;
    width:100%;
  }
  #bottom_bar{
    height:6%;
    width:100%;
    border-top:1px solid lightgray;
    background-color:rgb(251,252,252);
    vertical-align:bottom;
    display:inline-block;
  }
</style>
