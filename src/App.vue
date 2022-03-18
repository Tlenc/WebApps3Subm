<template>
<div id="app">

    <header>
      <h1>{{website.name}}</h1>
      <button v-on:click="website.showProduct = !website.showProduct">{{this.cart.length}} Checkout </button>
       </header>
       <lesson-list v-if="website.showProduct" :lessons="lessons" @addLesson="addItem"></lesson-list>
       <checkout v-if="!website.showProduct" :cart="cart" @removeLesson="removeFromCart" @passLessonToRemove="updateSpace"></checkout>
  </div>
</template>

<script>

import lessonList from './components/lesson_list.vue';
import checkout from './components/Checkout_form.vue';

export default {
  name: 'App',
  components: {
    checkout,
    lessonList
  },
  data() {
    return {
      lessons: {}, 
       cart: [{}], 
      website: {
        name: "Courses",
        showProduct: true
      },
      
    }
  },
  methods: {
    
       addItem(lessonPass) {
        this.cart.push(lessonPass);
        lessonPass.space--;
        console.log(lessonPass._id);
      },
    removeFromCart(lessonRemove){
     
        //      console.log(this.cart.length)

        // for(let i=0; i<this.cart.length;i++){
        //   if(this.cart[i]._id === lessonRemove._id){
        //     lessonRemove.space++;
        //     this.cart.splice(this.cart.indexOf(lessonRemove),1)
        //   }
        // }
        console.log(this.cart.indexOf(lessonRemove).subject);
        this.cart.splice(lessonRemove,1);
        

    },
    updateSpace(lesson){
      lesson.space++;
    },
    showCheckout() { this.website.showProduct === this.website.showProduct ? false : true;}}
    ,
 async created () {
     var vm = this;
       await fetch('https://web-apps-cw2.herokuapp.com/lesson').then(response => {
            response.json().then(
              function (json) {
                console.log(JSON.stringify(json));
                vm.lessons = json;
               
              });
          });
      }
    
  
};
</script>

<style>
#app {

  
}
</style>
