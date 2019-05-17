<template>
    <li>{{litext}}</li>
</template>
<script>
export default {
    created(){
        console.log(this);
       

      
    },
    data(){
        return{
            litext:this.$bur.litext
        }
    }
}
</script>
<style>

</style>
