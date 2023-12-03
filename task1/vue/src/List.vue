<template>
  <div class="wrapper" @click="handleItemClick">
    <div class="task">
      <div class="task__left">
        <div class="task__icon">
          <svg focusable="false" fill="#fff" width="24" height="24" viewBox="0 0 24 24" class=" NMm5M hhikbc"><path d="M7 15h7v2H7zm0-4h10v2H7zm0-4h10v2H7z"></path><path d="M19 3h-4.18C14.4 1.84 13.3 1 12 1c-1.3 0-2.4.84-2.82 2H5c-.14 0-.27.01-.4.04a2.008 2.008 0 0 0-1.44 1.19c-.1.23-.16.49-.16.77v14c0 .27.06.54.16.78s.25.45.43.64c.27.27.62.47 1.01.55.13.02.26.03.4.03h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-7-.25c.41 0 .75.34.75.75s-.34.75-.75.75-.75-.34-.75-.75.34-.75.75-.75zM19 19H5V5h14v14z"></path></svg>
        </div>
        <div class="task__option">
          <div class="task__title">
            {{ title }}
          </div>
          <div class="task__course">
            {{ course }}
          </div>
        </div>
      </div>
      <div class="task__right">
        <div class="task__deadline">
          {{ deadline }}
        </div>
      </div>
    </div>
   
  </div>
</template>

<script>
export default {
  data () {
    return {
    
    }
  } , 
  methods: {
    handleItemClick() {
      this.$emit('click', this.index); // Assuming you have an 'index' prop in app-item
    }
  } ,
  props: ['title' , 'course' , 'deadline']
}
</script>

<style>

  .task{
    width: 60% ; 
    margin: 2vh auto ; 
    margin-bottom: 0 ; 
    display: flex ; 
    border-bottom: 1px solid gray ; 
    padding-bottom: 2vh ; 
    justify-content: space-between ; 
  }



  .task__left{
    display: flex ; 
  }

  .task__icon{
    background: rgb(30,142,62) ; 
    align-self: start;
    border-radius: 50%;
    flex-shrink: 0;
    height: 2.25rem;
    width: 2.25rem;
    align-items: center;
    display: flex;
    justify-content: center;
    margin-right: 20px ;
  }

  .task__title{
    font-weight: 600 ; 
    font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
    color: #8c8c8c ;
    padding-bottom: 5px ;
  }

  .task__course{
    font-size: 14px ;
  }

</style>


