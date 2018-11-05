<template>
  <div id="hmbgr_template_div">
    <div id="hmbgr_sign_div">
      <div class="hmbgr-stripe"></div>
      <div class="hmbgr-stripe"></div>
      <div class="hmbgr-stripe"></div>
    </div>
    <img src="./assets/whatsapp-logo.png" /><br/>
    <img src="./assets/fbmessenger-logo.png" /><br/>
    <img src="./assets/viberr-logo.png" /><br/>
    <img src="./assets/skype-logo.png" /><br/>
  </div>
</template>

<script>
  export default{
    data(){
      return {
        greeting:'Merhaba!'
      }
    }
  }
</script>

<style scoped>
  #hmbgr_template_div{
    width:4%;
    height:100%;
    float:left;
    background-color:rgba(35,35,35);
    color:white;
  }
  #hmbgr_sign_div{
    height:2.3%;
    margin-bottom:40%;
    margin-left:25%;
    margin-top:25%;
  }
  .hmbgr-stripe{
    background:#dbdbdb;
    width:50%;
    height:22%;
    margin-top:10%;
    border-radius:16%;
  }
  img{
    padding-top:5%;
    width:50%;
    margin-bottom:24px;
  }
</style>
