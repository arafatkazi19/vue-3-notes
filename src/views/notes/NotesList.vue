<template>
<div>
  <div v-for="(note,index) in notes" :key="index">
    <h1>{{note.title}}</h1>
  </div>
</div>
</template>

<script>
import axios from 'axios';
import {onMounted,reactive} from 'vue'

export default {
  name: 'NotesList',
  setup() {
    const state = reactive({
      notes:[]
    });
    onMounted(async () => {
      const res = await axios.get('http://localhost/NotesCake/notes');
      state.notes = res.data.notes;
      console.log(res.data.notes)

    });

    return {onMounted}
  }
};
</script>

<style scoped>

</style>