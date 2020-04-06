<template>
  <div id="app">
   <h3>{{titletodo}}</h3>
   <span>
   <input type="text" v-model="addTask">
    <button class="clicktask" @click="task">ADD TODO</button>
    </span>

    <div class="item"
     v-bind:class="{completed: item.completed
     }"
     v-for="item in items" 
     v-bind:key="item.id">
      <h2>{{item.title}}</h2>
      <button class="ready" v-if="!item.completed"
       @click="removeItem(item.id)">READY</button>
      </div>
  </div>
</template>
<script>
export default {
data(){
  return{
    titletodo:'TODO LIST',
    addTask:'',
    items:[
      {title:'buy milk',completed: false,id:'jnnjn'},
      {title:'add task',completed: false,id:'hjbhj'}
    ]
  }
},
methods:{
  task(){
    this.items.push({
     title:this.addTask,
     completed:false,
     id: Math.random()
    })
    this.addTask=''
  },
  removeItem(id){
  const index = this.items.findIndex(el => el.id === id)
  this.items[index].completed = true
}
}
}
</script>

<style>
#app{
  border:2px dotted red;
  border-radius: 10px;
  margin-left: 60px;
  margin-right: 60px;
  padding-left: 10px;
  padding-right: 10px;
  text-align: center;
}
.ready{
  border:1px solid black;
  border-radius: 10px;
  padding: 5px 10px;
  background-image: linear-gradient(to right,#cc2e5d,#ff5858);
  font-size: 16px;
}
.ready:hover{
  color:white;
  cursor:pointer;
}
.item{
  border:1px solid black;
  border-radius: 10px;
  margin:8px;
  padding:10px;

}
.completed{
  opacity:0.5;
}
.completed h2{
  text-decoration:line-through;
}
h3{
  text-align: center;
  font-weight: 700;
  font-size: 30px;
}
input{
  border:1px solid black;
  padding:10px 20px;
  margin-right: 5px;
  border-radius: 8px;
}
.clicktask{
  border:1px solid black;
  border-radius: 8px;
  padding: 10px 20px;
  background-image: linear-gradient(to right,#cc2e5d,#ff5858);
  color:white;
  font-size: 18px;
  font-weight: 700;
  box-shadow: 3px 3px rgb(0,0,0,0.4);
  font-family: 'Times New Roman', Times, serif;
  transition: 0.3s ease-out;
}
.clicktask:hover{
  box-shadow: 6px 6px rgba(0,0,0,0.6);
  cursor:pointer;
}
</style>


