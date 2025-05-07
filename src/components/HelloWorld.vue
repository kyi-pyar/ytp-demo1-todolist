<template>
  <v-container>
    <h2>{{ title }}</h2>           
    <v-text-field label="Enter your name" :disabled="flag" v-model="name" @keydown.enter="changeFlag"></v-text-field>
    <v-btn rounded="xl" size="x-large" block @click="changeFlag" color="primary">Click Me</v-btn>
    <br>
    <h3 > Hello: {{ name }}</h3>
    <br>
    <v-text-field label="What do you do?"  v-model="description" ></v-text-field>
    <v-text-field label="How long it takes?" v-model="duration"></v-text-field>
    <v-btn @click="addToDo" prepend-icon="mdi-plus"></v-btn>     
  <v-table>
    <thead>
      <tr>
        <th class="text-left">
          No:
        </th>
        <th class="text-left">
          Description
        </th>
        <th class="text-left">
          Duration
        </th>
        <th class="text-left">
          Date
        </th>
        <th class="text-left">
          Remark
        </th>
        
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="todo in list"
        :key="todo.id"
      >
        <td>{{ todo.id }}</td>
         <td>{{ todo.des }}</td>
        <td>{{ todo.time }} hours</td>
        <td>{{ todo.date }} </td>
        <td v-if=" todo.time <=2 " >Active </td>
        <td v-else> Tired </td> 
        <td><v-btn @click="deleteToDo(todo)" append-icon="mdi-delete"></v-btn></td>      
      </tr>
    </tbody>
  </v-table>
  </v-container>
</template>
<script>
export default {
  name: 'HelloWorld',
  data: () => ({   
    title:"This is First Vue Test.",
    flag:true,
    name:"",
    list:[
      {id:1, des: "Learning Vue", time: 2, date: new Date().toDateString()},
      {id:2, des: "Shopping", time: 3, date: new Date().toDateString()}
    ],
    description:"",
    duration:0
  }),
  methods:{
    changeFlag(){
      this.flag=!this.flag
    },
    addToDo(){
      this.list.push({id:this.list.length+1,des:this.description,time:this.duration, date: new Date().toDateString()})      
    },
    deleteToDo(todo){
      //this.list.pop();
      this.list=this.list.filter( td => td.id != todo.id)
    },   
  }
}
</script>
