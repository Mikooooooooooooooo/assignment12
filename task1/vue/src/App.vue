
 

<template>
    <div>

      <div class="header">
        <div class="header__title" >
          Task List
        </div>
      </div>


      <div class="subheader">
        <div class="parts">
          <div class="part" id="assig" @click="to_assigned">
            Assigned
          </div>
          <div class="part" id="done" @click="to_done">
            Done
          </div>
        </div>
        <div class="input">
          <input type="text" v-model="new_title" placeholder="Enter new task's title">
          <input type="text" v-model="new_course" placeholder="Enter new task's course">
          <input type="text" v-model="new_deadline" placeholder="Enter new task's deadline">
          <button v-on:click="accept">add</button>
        </div>
      </div>


      <div class="main">
        <div class="nonCompleted" v-if="show">
            <app-item v-for="(item, index) in items" :title="item.title" :course="item.course" :deadline="item.deadline" @click="changeInItem(index)">
          
            </app-item>
        </div>
        <div class="completed" v-else>
            <app-item v-for="(compl, index) in completedItems" :title="compl.title" :course="compl.course" :deadline="compl.deadline" @click="changeInCompl(index)">

            </app-item>
        </div>
      </div>
    </div> 
</template>

<script>

import Item from './List.vue'  

export default {
  data () {
    return {
      items: [
        {title: 'Do Assignment 12' , course: 'INF 231' , deadline: 'Thursday , 11:59pm' ,  isCompleted: false } , 
        {title: 'Make solution video ' , course: 'CSS 215' , deadline: 'Tuesday , 11:59pm' , isCompleted: false } , 
        {title: 'Solve LeetCode problem' , course: 'CSS 215' ,deadline: '10 December , 11:59pm' , isCompleted: false } , 
        {title: 'Preparing for a quiz' , course: 'MAT 234' , deadline: 'Wednesday , 11:59pm' , isCompleted: false } , 
        {title: 'Make a video ' , course: 'MDE 231' , deadline: 'Saturday , 11:59pm' , isCompleted: false }  
      ] , 
      completedItems: [] , 
      temp:[] ,
      new_title: '' ,
      new_course: '' ,
      new_deadline: '' ,
      show: true 
    }
  } , 
  components: {
    'app-item' : Item  
  } , 
  methods: {
    changeInItem(index){
      this.completedItems.push(this.items[index]) ; 
      console.log(this.completedItems)
      this.items.splice(index,1)  
    } , 
    changeInCompl(index){
      this.items.push(this.completedItems[index]) ; 
      this.completedItems.splice(index,1)  
    } ,
    to_done(){
      this.show = false
      const title_ass = document.querySelector('#assig') ; 
      const title_done = document.querySelector('#done') ; 

      title_ass.style.color = "#575757" ; 
      title_done.style.color = "#0c7df5" ;
    } ,
    to_assigned(){
      this.show = true 
      const title_ass = document.querySelector('#assig') ; 
      const title_done = document.querySelector('#done') ; 

      title_ass.style.color = "#0c7df5" ; 
      title_done.style.color = "#575757" ;
    } , 
    accept(){
      if (this.new_course.length == 0 || this.new_deadline.length == 0 || this.new_title.length == 0)
        alert('Enter all data')
      else {
        const new_task = {title: this.new_title , course: this.new_course , deadline: this.new_deadline , isCompleted: false} ; 
        this.items.push(new_task) ;
        this.new_course = '' ; 
        this.new_deadline = '' ;
        this.new_title = '' ; 
      }
    }
  }
}
</script>

<style>

  body{
    margin: 0 ; 
    padding: 0 ; 
  }

  *{
    box-sizing: border-box ; 
  }

  .container{
    width: 80% ; 
    margin: 0 auto ; 
  }

  .header{
    padding: 2vh 5%; 
    border-bottom: 1px solid #a2a3a2 ; 
  }

  .header__title{
    font-size: 24px ; 
    font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif ; 
    color: #a2a3a2;
  }

  #assig{
    color: #0c7df5; 
  }

  .parts{
    padding: 0 3% ; 
    display: flex ; 
  }

  .part{
    padding: 10px ; 
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif ; 
    font-size: 14px ;
    font-weight: 500 ; 
    color:  #575757 ; 
  }

  .part:hover{
    background: #f5f5f5 ; 
    cursor: pointer ; 
  }

  .main{
    margin-top: 5vh ; 
  }

  .list__title{
    font-size: 24px ; 
    font-weight: 500 ; 
  }

  .subheader{
    display: flex ; 
    justify-content: space-between ; 
  }

  .input{
    padding: 10px 2% ; 
  }

  .input input{
    width: 240px ; 
    padding: 2px 10px ; 
  }

</style>

