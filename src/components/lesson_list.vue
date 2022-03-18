<template>
<main>
<div v-for="lesson in lessons" :key="lesson._id">
        
        <figure>
          <img style="width: 200px;" v-bind:src="'https://web-apps-cw2.herokuapp.com/' + lesson.image">
        </figure>
        <p>Subject: {{lesson.subject}}</p>
        <p>Location: {{lesson.location}}</p>
        <p>Price : {{lesson.price}}</p>
        <p>Availabe spaces : {{lesson.space}}</p>

        <button key="lesson.icon" @click='addLesson(lesson)'>
          <i class="lesson.icon"></i>
          Add Lesson
        </button>

     

          <!--spawning lessons from lessons.js, implementing search and add to cart button with checks of availability and lesson div visability -->
</div>
</main>
</template>

<script>

export default {
    
   
  name: 'lessonList',
  props: ['lessons'],
  data() {
    return {
      
    }
  },
   
  methods: 
  {
      
       addLesson(lessonPass) {
        this.$emit('addLesson',lessonPass)
      }
 

}
}
</script>

<style>
#app {
  
}
</style>
