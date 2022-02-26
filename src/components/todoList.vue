<template>
    <nav class="col-6 mb-3">
        <div class="nav nav-tabs" id="nav-tab" role="tablist">
            <a class="nav-item nav-link active font-weight-bold" id="nav-home-tab">undone <span class="badge badge-secondary">9</span></a>
            <a class="nav-item nav-link font-weight-bold" id="nav-profile-tab">done <span class="badge badge-success">9</span></a>
        </div>
<!--      {{this.newtext}}-->
    </nav>
    <todos
        v-for="(item , index) in todos"
        :todo="item" :key="index"
        @deleteTodo="$emit('deletee' , item)"
        @ediiting="$emit('editt' , $event  ,item)"
    />


</template>

<script>
import Todos from './todos.vue'

export default {
    components:{
        Todos

    } ,
    props:{
        todos:{
            type:Array
            }
        } ,
  methods:{
  // sahand(newtext){
  //   this.$emit('editt' , newtext  ,item)
  // }
  }
}
</script>

<style>

</style>