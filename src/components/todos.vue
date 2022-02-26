<template>
    <div class="col-6 mb-2">
    <div class="d-flex justify-content-between align-items-center border rounded p-3">
        <div>
            <span  v-show="!editSate">
              {{todo.text}}
             </span>

            <span  v-show="editSate" >
              <input class="form-control" type="text" v-model='newtext'  >
            </span>

        </div>
        <div>
            <button class="btn btn-info btn-sm"        @click="editing">{{blueButton}}</button>
            <button class="btn btn-danger btn-sm ml-1" @click="$emit('deleteTodo')">delete</button>

       </div>
        </div>
    </div>
</template>

<script>
export default {
        data(){
            return{
              editSate :false ,
              blueButton : 'edit' ,
              newtext : ''
            }
        } ,
        props:{
            todo:{
                type:Object
            }
        },
        methods:{
          editing(){
              this.editSate =!this.editSate ;
              this.$emit('ediiting' ,this.newtext)
              if(this.blueButton =='edit') {
                this.blueButton ='done'

              }else {
                this.blueButton ='edit'
              }

          } ,

        } ,
       provide:{
          delsa:'gogosh'
         } ,





}
</script>

<style>

</style>