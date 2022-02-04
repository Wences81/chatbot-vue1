<template>
    
      <div class=''>{{info}}
        <p 
        class="questions"></p>

          <ul class='answers'>

              <li          
               class="answer"
               v-for="(answer, idx) in answers"
               :key="idx"
               >
                 
                   <p class="value">
                       {{}}
                   </p>

                   <p class="title">
                      {{}}
                   </p>

              </li>
              <li class='messages'>
                   <p class="message-value">
                       {{info.value}}
                   </p>
                   <p class="message-title">
                      {{}}
                   </p>

              </li>

          </ul>

      </div>
     
 
</template>

<script>
import axios from 'axios'


export default {
  name: 'ChatBot',
  data: () => ({  
  info: '',
  info: [],
  // value:'',
  // questions: [],
  answers: []
    
  }),

mounted() {
  axios.get('https://618404bd91d76c00172d1d23.mockapi.io/api/chat')
  .then(response => (this.info = response.data))

  .catch(error => console.log(error))

  } 
}

</script>

<style>

</style>