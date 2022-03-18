<template>
    <div>
    <h2>Checkout</h2>
    <h3>Added lessons</h3>
    <div  v-for="(lesson, index) in cart" :key="lesson._id">
       <figure>
          <img style="width: 200px;" v-bind:src="'https://web-apps-cw2.herokuapp.com/' + lesson.image">
        </figure>
        {{lesson.subject}} 
        <button @click='removeLesson(index); passLessonToRemove(lesson)'>Remove</button>
    </div>
    <p>
    <strong>Name</strong> <input v-model="name" />
    <strong>Adress</strong> <input v-model="address" />
    <button>Submit</button>
    </p>
    </div>
</template>

<script>
export default {
    name : 'Checkout_form',
    props: ['cart'],
    data(){
        return{
            name: "",
            address: ""
        };
    },
 methods: {
    removeLesson(lessonRemove){
        this.$emit('removeLesson',lessonRemove,)
        
    },
    passLessonToRemove(lesson){
        this.$emit('passLessonToRemove',lesson,)
    }
 }
};
</script>
