<template>
  <v-container>
    <h2>{{ title }}</h2>           
    <v-text-field label="Enter your name" :disabled="flag" v-model="name" @keydown.enter="changeFlag"></v-text-field>
    <v-btn rounded="xl" size="x-large" block @click="changeFlag">Click Me</v-btn>
    <br>
    <h3> Hello: {{ name }}</h3>
    <br>

    <table border="2" >
      <tr>
        <th>Descirption</th>
        <th>Duration</th>
        <th>Date</th>
      </tr>
      <tr v-for="todo in list" :key="todo.des">
        <td>{{ todo.des }}</td>
        <td>{{ todo.time }} hours</td>
        <td>{{ todo.date }}</td>
      </tr>
    </table>
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
      {des: "Learning Vue", time: 2, date: new Date()},
      {des: "Shopping", time: 3, date: new Date()}
    ]
  }),
  methods:{
    changeFlag(){
      this.flag=!this.flag
    }
  }
}
</script>
