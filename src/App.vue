<template>
  <div id="app">
    <h2>已选择：</h2>
    <div v-for="(val,ind) in list" 
    v-if="val.arr.length"
    :key="ind+1000">
      <span v-for="(item,i) in val.arr" 
      :key="i+2000">{{item.text}}</span>
      <span @click="isAll({index:ind})">X</span>
    </div>
    <mytab v-for="(item,i) in list" 
    @addClass="addClass"
    @clear="isAll"
    :index="i"
    :key="i" 
    :item="item">

    </mytab>
    
  </div>
</template>

<script>
import mytab from "./components/mytab.vue";
import list from "./data/list.js";
export default {
  name: 'App',
  methods:{
    addClass(obj){
      let {index,i,type,text} = obj;
      if(type === "radio"){
        this.$set(this.list[index].arr,"0",{text,i});
      }else{
        if(!this.list[index].arr.find(item=>item.i===i)){
        this.list[index].arr.push({text,i});
        }else{
          let indexac = this.list[index].arr.findIndex(item=>item.i===i)
           this.list[index].arr.splice(indexac,1);
        }
      }
    },
    isAll(obj){
      let {index} = obj;
      this.$set(this.list[index],"arr",[]);
    }
    
  },
  components:{
    mytab
  },
  data(){
    return {
        list:list
    }
  }  
}
</script>

<style>
  span.active{
    color: aqua;
    background:skyblue;
  }
</style>
