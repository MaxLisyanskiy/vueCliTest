<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">
          <h1>{{title}}</h1>

          <message v-if="message" :message="message"/>
          
          <!--new note-->
          <div class="new-note">
              <input v-model="note.title" type="text">
              <textarea v-model="note.descr"></textarea>
              <button @click="addNote">New note!</button>
          </div>
          <!--notes-->
          <div class="notes">
              <div class="note" v-for="(note, index) in notes" :key="index" style="border: 1px solid grey; width: 20%;">
                  <div class="note-header">
                      <p>{{note.title}}</p>
                  </div>
                  <div class="note-body">
                      <span>{{note.descr}}</span>
                      <p>{{note.date}}</p>
                  </div>
              </div>
          </div>
        </div>
      </section>

    </div>  
  </div>
</template>

<script>
import message from "@/components/Message.vue"

export default {
  components: {
    message
  },
  data() {
    return {
      title: 'Notes App',
        message: null,
        note: {
            title: '',
            descr: ''
        },
        notes: [
              {
                  title: "first note",
                  descr: "first descr",
                  date: new Date(Date.now()).toLocaleString()
              },
              {
                  title: "second note",
                  descr: "second descr",
                  date: new Date(Date.now()).toLocaleString()
              },
              {
                  title: "third note",
                  descr: "third descr",
                  date: new Date(Date.now()).toLocaleString()
              }
          ]
      }
    },
    methods: {
      addNote() {
        let {title, descr} = this.note;

        if(title === '') {
            this.message = 'Title is null'
            return false;
        }
        
        this.notes.push({
            title,
            descr,
            date: new Date(Date.now()).toLocaleString()
        })
        this.message = null;
        this.note.title = '';
        this.note.descr = '';
      }
    }
}
</script>


<style>
</style>
