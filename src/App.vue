
<template>
  <div class = "app">
    <p>{{ name }} -- {{ count }}</p>
    <button @click="changeName('Changed!')"> Change Name</button>
    <button @click="onCount()"> Count Button</button>
  </div>
</template>



<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name:'App',
  components:{},
  data(){
    return{
      name : 'Default!',
      count: 1,
    } ;
  },
  methods:{
    changeName(newName: string){
      if(this.name == 'Default!' ){
        this.name = newName;
      }
      else{
        this.name = 'Default!';
      }
     
    },
    onCount() {
    this.count += 1;
    }

  }
});
</script>


<style>

</style>