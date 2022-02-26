<template>
   <section class="jumbotron">
        <div class="container d-flex flex-column align-items-center">
            <h1 class="jumbotron-heading">Welcome!</h1>
            <p class="lead text-muted">To get started, add some items to your list:</p>
            <div class="form-inline">
                <div class="form-group">
                    <input type="text" v-model='message' class="form-control mx-sm-3" placeholder="I want to do ...">
                    <button @click="$emit('addTodo' ,message)" class="btn btn-primary">add</button>
                </div>
            </div>
               
        </div>
    </section>
</template>

<script>
export default {
    data(){
     return{
         message: ''
     }
    } ,

}
</script>

<style>
.jumbotron-heading{
  color: red;
}
</style>