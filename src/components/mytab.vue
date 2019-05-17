<template>
<div>
    <myli></myli>
<h2>{{item.title}}</h2>
    <div>
        <span :class="{active:item.arr.length==0}"
        @click="clear"
        >不限</span>
        <span v-for="(val,i) in item.content"
        @click="tab(val,i)"
        :class="{active:item.arr.find(item=>item.i == i)}"
         :key="i">{{val.text}}</span>

    </div>
</div>
    
    
</template>
<script>
import myli from "./myli.vue";
export default {
    props:{
        item:Object,
        index:Number
    },
    components:{
        myli
    },
    methods:{
        tab(val,i){
            this.$emit("addClass",{index:this.index,text:val.text,i:i,type:this.item.type});
        },
        clear(){
             this.$emit("clear",{index:this.index});
        }
        
    }

}
</script>
<style>
    span{
        display: inline-block;
        padding:2px 10px;
        margin:3px;
        border:1px solid #ccc;
    }
    span.active{
        background:skyblue;
        color:white;
    }
</style>
