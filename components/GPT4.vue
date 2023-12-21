<template>
  <div class="gpt4-container">
    <textarea v-model="userInput" placeholder="Enter your message"></textarea>
    <button @click="sendMessage">Send Message</button>
    <div v-if="response" class="response">{{ response }}</div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios';

const userInput = ref('');
const response = ref('');
const messages = ref([]);

const sendMessage = async () => {
  messages.value.push({ role: 'user', content: userInput.value });

  try {
    const data = {
      model: "gpt-3.5-turbo-0613",
      messages: messages.value,
    };

    const result = await axios.post('https://api.openai.com/v1/chat/completions', data, {
      headers: {
        'Authorization': `Bearer ${import.meta.env.VITE_OPENAI_API_KEY}`,
        'Content-Type': 'application/json'
      }
    });

    response.value = `AI: ${result.data.choices[0].message.content}`; // Update to show only the latest response
    userInput.value = ''; // Clear input after sending
  } catch (error) {
    console.error('Error calling OpenAI Chat:', error);
    response.value = 'Error: Unable to fetch response'; // Clear previous response and show error
  }
};
</script>

<style scoped>
.gpt4-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

textarea {
  width: 100%;
  margin-bottom: 1rem;
  padding: 1rem;
  border: 1px solid #000;
}

.response {
  margin-top: 1rem;
  border: 1px solid #953d3d;
  padding: 1rem;
  max-height: 200px; /* Maximum height for the response box */
  overflow-y: auto; /* Enable vertical scrollbar if content exceeds max height */
}
</style>
