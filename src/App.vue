<template>
  <headerr />
  <h1>{{delsa}}</h1>
  <teleport to="body">
    <sloti>
      <div class="alert alert-success" role="alert">
        <h4 class="alert-heading">ziba done!</h4>
        <p>Aww NO, you DAYLA read this important alert message. This example text is going to run a bit longer so that you can see how spacing within an alert works with this kind of content.</p>
        <hr>
      </div>
    </sloti>

    <sloti>
      <div class="alert alert-success" role="alert">
        <h4 class="alert-heading">Well done!</h4>
        <hr>
        <p class="mb-0">coron.</p>

      </div>
    </sloti>
    <sloti></sloti>
    <sloti>
      <div class="alert alert-success" role="alert">
        <h4 class="alert-heading">zesht bahs</h4>
        <p>Aww yeah, you successfully read this important alert message. This example text is going to run a bit longer so that you can see how spacing within an alert works with this kind of content.</p>
        <hr>
      </div>
    </sloti>

  </teleport>

  <welcome  @addTodo="adding"/>
    <div class="todoList">
      <div class="container">
          <div class="d-flex flex-column align-items-center">
                <todolist
                    :todos="todos"
                     @deletee="Deleting"
                    @editt="edito"
                ></todolist>
            </div>
       </div>
    </div>
</template>


<script>
  import headerrVue from "./components/headerr.vue"
  import welcome from "./components/welcome.vue"
  import todosVue from "./components/todos.vue"
  import todoListVue from "./components/todoList.vue"
  import slot from './components/slot.vue'
  import  axios from 'axios'

    export default{
      created() {
        axios.get('https://vue-project-8e390-default-rtdb.europe-west1.firebasedatabase.app/ziba.json')
        .then(res=>{
          Object.entries(res.data).forEach(val =>{
            this.todos.push({
              key:val[0] ,
              done:false ,
              text:val[1].text
            })
          })
        })
      } ,
      components:{
        'headerr' :headerrVue ,
        'welcome':welcome ,
        'todos' : todosVue ,
        'todolist'  :todoListVue  ,
        'sloti' :slot
      }  ,
      data(){
        return{
          todos :[ ]
        }
      },
       methods:{
       adding(text){
         let assets={
           done:false ,
           text
         }
         axios.post('https://vue-project-8e390-default-rtdb.europe-west1.firebasedatabase.app/ziba.json' , assets )
         .then(res =>{
           console.log(res)
           this.todos.push({
             ...assets ,
             key:res.data.name ,
           })
         })
         .catch(err =>console.log(err))
     } ,
       Deleting(item){
         axios.delete(`https://vue-project-8e390-default-rtdb.europe-west1.firebasedatabase.app/ziba/${item.key}.json`)
       this.todos = this.todos.filter(todo =>todo !==item)
     } ,
       edito(newtext ,item) {
         axios.patch(`https://vue-project-8e390-default-rtdb.europe-west1.firebasedatabase.app/ziba/${item.key}.json` ,{text:newtext})
         let yy = this.todos.filter((u) => u == item)
         yy[0].text = newtext
         inject:['delsa']
         console.log(newtext );
       }
      }
    }
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
