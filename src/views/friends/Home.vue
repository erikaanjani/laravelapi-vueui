<template>
 <div class="home">
    <Slider />
    <hr class="my-3">
      <router-link class="btn btn-primary" to="/createfriends">ADD FRIEND</router-link>
      <router-link class="btn btn-primary" to="/createfriends"
      >ADD FRIEND</router-link
      >

      <Cardfriends :friends="friends" />

    <table class="table">
  <thead>
    <tr>
@@ -34,16 +39,19 @@
import axios from 'axios'
// @ is an alias to /src
import Slider from "@/components/Slider.vue";
import { ref, onMounted } from 'vue';
import Cardfriends from "@/components/Cardfriends.vue";
import { onMounted, ref } from 'vue';
export default {
  name: "Home",
  components: {
    Slider
    Slider,
Cardfriends,
  },
  setup(){
    let friends = ref([])
    onMounted(() => {
      axios.get('http://pia.labirin.co.id/api/friends')
      axios.get('http://127.0.0.1:8000/api/friends')
      .then(response => {
        friends.value = response.data.data
      })
@@ -53,7 +61,7 @@ export default {
    })
    function friendDelete(id){
      axios.delete(`http://pia.labirin.co.id/api/friends/${id}`)
      axios.delete(`http://127.0.0.1:8000/api/friends/${id}`)
      .then(()=>{
        let z = this.friends.map(friends => friends.id).indexOf(id);
        this.friends.splice(z, 1)