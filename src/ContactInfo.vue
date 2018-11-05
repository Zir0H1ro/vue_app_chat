<template>
  <div id="contact_info_div">
    <img id="contact_main_img" v-bind:src=contacts[0].picUrl />
    <h3 id="contact_name"><b>{{contacts[0].name}}</b></h3>
    <h4 id="contact_location">{{contacts[0].location}}</h4>
  </div>
</template>

<script>
  import {event_bus} from './main';

  export default{
    props:['contacts'],
    data(){
      return {

      }
    },
    created(){
      event_bus.$on('select_contact', (data) => {
        let my_cont = document.getElementById('contact_info_div');
        my_cont.innerHTML = '<img id="contact_main_img" src="' + this.contacts[data].picUrl + '" />' +
        '<h3 id="contact_name"><b>' + this.contacts[data].name + '</b></h3>' +
        '<h4 id="contact_location">' + this.contacts[data].location + '</h4>';

      });
    }
  }
</script>

<style scoped>
    #contact_info_div{
      display:inline-block;
    }
</style>
