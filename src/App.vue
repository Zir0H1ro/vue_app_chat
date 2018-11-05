<template>
  <div id="app">
    <hmbgr-menu></hmbgr-menu>
    <msgs-and-search v-bind:contacts="contacts" v-on:select_contact="selectContact($event)"></msgs-and-search>
    <msg-panel v-bind:contacts="contacts"></msg-panel>
    <contact-info v-bind:contacts="contacts"></contact-info>
  </div>
</template>

<script>
import HmbgrMenu from './HmbgrMenu.vue'
import MsgsAndSearch from './MsgsAndSearch.vue'
import MsgPanel from './MsgPanel.vue'
import ContactInfo from './ContactInfo.vue'

export default {
  name: 'app',
  components:{
    'hmbgr-menu':HmbgrMenu,
    'msgs-and-search':MsgsAndSearch,
    'msg-panel':MsgPanel,
    'contact-info':ContactInfo
  },
  data () {
    return {
      contacts:[
        {name:'Danny Rand', picUrl:'./src/assets/danny-rand.jpg',location:'K\'un Lun, Himalaya, Nepal', msgs:[{text:'Hi, it\'s Danny. Please get back to me as soon as you can.',type:'received'}]},
        {name:'Colleen Wing', picUrl:'./src/assets/colleen-wing.jpeg', location:'Manhattan, New York City, NY' ,msgs:[{text:'Hello, I\'m Colleen from Chikara Dojo. Thanks for reaching out! What can I do for you?',type:'received'}]},
        {name:'Ward Meachum', picUrl: './src/assets/ward-meachum.jpg', location:'Rand Enterprises, New York City, NY', msgs:[{text:'This is Ward Meachum of Rand Enterprises. Would you like to hear about investment options?',type:'received'}]},
        {name:'Joy Meachum', picUrl: './src/assets/Joy_Meachum_S2.jpg', location:'Rand Enterprises, New York City, NY', msgs:[{text:'Hi, it\'s Joy. Have you heard from Danny lately? I\'m a little bit worried about him.',type:'received'}]}
      ]
    }
  },
  computed:{
    isShowDetails:function(){
      alert(window.innerWidth >= 1200);
      return (window.innerWidth >= 1200);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height:100%;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
