<template>
  <div class="chat-container">
    <header class="chat-header">
      <h1>LINE風チャット</h1>
    </header>
    <div class="chat-messages">
      <div v-for="(message, index) in messages" :key="index" :class="{'my-message': message.isMine, 'other-message': !message.isMine}">
        <span>{{ message.text }}</span>
      </div>
    </div>
    <div class="message-input">
      <input type="text" v-model="newMessage" @keyup.enter="sendMessage" placeholder="メッセージを入力...">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newMessage: '',
      messages: [
        { text: 'こんにちは！', isMine: false },
        { text: 'こんにちは、元気ですか？', isMine: true }
        // 他のメッセージ...
      ]
    };
  },
  methods: {
    sendMessage() {
      if (this.newMessage.trim() !== '') {
        this.messages.push({ text: this.newMessage, isMine: true });
        this.newMessage = '';
      }
    }
  }
};
</script>

<style>
.chat-container {
  max-width: 600px;
  margin: auto;
  border: 1px solid #ddd;
  height: 90vh;
  display: flex;
  flex-direction: column;
}

.chat-header {
  background-color: #00B900;
  color: white;
  text-align: center;
  padding: 10px;
}

.chat-messages {
  flex-grow: 1;
  overflow-y: scroll;
  padding: 10px;
}

.chat-messages div {
  margin-bottom: 10px;
  padding: 5px;
  max-width: 70%;
  word-break: break-word;
}

.my-message {
  background-color: #DCF8C6;
  margin-left: auto;
  border-radius: 10px;
}

.other-message {
  background-color: #FFFFFF;
  border-radius: 10px;
}

.message-input {
  padding: 10px;
  background-color: #f4f4f4;
}

.message-input input {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
}
</style>
