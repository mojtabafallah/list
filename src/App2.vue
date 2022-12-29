<script>
export default{
    data(){
        return{
           value:'' 
        }
    }
}
</script>

<template>
    <input :class="value ? 'not-empty' : 'empty'" v-model='value'>
    <p>{{value}}</p>
</template>

<style>
  .empty{
    border : 1px solid red;
    background-color :red;
  }
  
  .not-empty{
    border : 1px solid green;

    background-color  : green
  }
</style>