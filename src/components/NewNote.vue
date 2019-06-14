<template>
   <!-- new note -->
  <div class="new-note">

    <!-- title -->
    <label class="title-input" >Title</label>
    <input class="title-input" v-model="note.title" type="text">

    <!-- priority -->
    <div class="priority-wrapper">
      <div class="priority" v-for="(item, index) in priority" :key="index" >
        <input type="radio" v-model="note.priority" :id="index" name="priority" :value="item">
        <label :for="index" :class="item"> {{ item }} </label>
      </div>
    </div>
    
    <!-- description -->
    <label>Description</label>
    <textarea v-model="note.descr"></textarea>
    <button class="btn btnPrimary" @click="addNote">New note</button>
  </div>
 </template>
 
 <script>
 export default {
   props: {
     note: {
       type: Object,
       required: true
     },
     priority: {
       type: Array,
       required: true
     }
   },
   methods: {
     addNote () {
       this.$emit('addNote', this.note)
     }
   }
 }
 </script>

 <style lang="scss">
  .new-note {
    text-align: center;
  }

  .priority-wrapper {
  width: 50%;
  display: flex;
  justify-content: space-around;
  margin: 0 auto 20px;
  }
 </style>
 
 