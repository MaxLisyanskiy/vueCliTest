<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">
          <h1>{{title}}</h1>

          <!--message-->
          <message v-if="message" :message="message"/>

          <!--new note-->
          <newNote 
            :note="note"
            @addNewNote = "addNote"
          />

          <!--notes-->
          <notes :notes="notes" @remove="removeOldNote"/>
          
        </div>
      </section>

    </div>  
  </div>
</template>

<script>
import message from "@/components/Message.vue"
import newNote from "@/components/NewNote.vue"
import notes from "@/components/Notes.vue"

export default {
  components: {
    message, newNote, notes
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
      },
      removeOldNote(index) {
        this.notes.splice(index, 1)
      }
    }
}
</script>


<style>
</style>
