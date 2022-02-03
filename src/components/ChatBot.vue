<template>
    <section class='chat-bot'>
      <div class='chat-bot-list-container' ref='chatbot'>
          <ul class='chat-bot-list'>
              <li class='message'
                  v-for='(message, idx) of messages'
                  :key='idx'
                   :class='message.author'
                   >
                   <p>
                       <span>{{ message.text}}</span>
                   </p>

              </li>

          </ul>

      </div>
      <div class='chat-inputs'>

          <input type="text" 
          v-model='message'
          @keyup.enter='sendMessage'
          />
              
            <button @click="sendMessage">Send</button>

      </div>

  </section>
</template>

<script>
export default {
  name: 'ChatBot',
  data: () => ({
    message: '',
    messages: []
  }),
  methods: {
    sendMessage() {
      const message = this.message
      
      this.messages.push({
        text: message,
        author: 'client'
        
      })
      this.message = ''
      this.$axios.get(`https://618404bd91d76c00172d1d23.mockapi.io/api/chat`)
       .then(res => res.json())
       console.log(json)
      .then(res => {
        this.messages.push({
          text: res.data.output,
          author: 'server'
        })
        this.$nextTick(() => {
          this.$refs.chatbot.scrollTop = this.$refs.chatbot.scrollHeight
        })
      })
    }
  }
}
</script>

<style>

</style>