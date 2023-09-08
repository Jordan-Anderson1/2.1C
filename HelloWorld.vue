<template>
  <div class="hello">
    <h1>User Input Form</h1>
    <form @submit.prevent="submitForm">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="name" required><br>

        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>

        <label for="message">Message:</label><br>
        <textarea id="message" v-model="message" cols="30" rows="14" required></textarea><br>

        <label for="subscribe">Subscribe to newsletter</label>
        <input type="checkbox" id="subscribe" v-model="subscribe"><br>

        <button type="submit">Submit</button>
    
    
    
    </form>

    <div v-if="submitted">
        <h2>Submitted Data:</h2>
        <p><Strong>Name:</Strong>{{ name }}</p>
        <p><Strong>Email:</Strong>{{ email }}</p>
        <p><Strong>Message:</Strong>{{ message }}</p>
        <p><Strong>Subscribed:</Strong>{{ subscribe ? 'yes' : 'no' }}</p>

    </div>
    <div v-else>
        <h2>Submitted Data:</h2>
        <p>Nothing yet submitted</p>
    </div>

    <div v-show="submitted">
        <p>You've submitted the form!</p>
    </div>

    

    
    <div v-if="submitted">
        <h1>Here's some useful links!</h1>
        <li v-for="link in links" :key="link">
            {{ link }}
        </li>
    </div>
    
</div>
  
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      message: '',
      subscribe: false,
      submitted: false,
      links: [
        'deakin.edu.au',
        'ontrack.deakin.edu.au'
      ]
    }
  },
  methods: {
    submitForm() {
      this.submitted = true;
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body, h1, p, label, button {
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    background-color: #ffffff;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    font-size: 24px;
    margin-bottom: 20px;
}

form {
    margin-top: 20px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="text"],
input[type="email"],
textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
}

input[type="checkbox"] {
    margin-top: 5px;
}

button {
    background-color: #007BFF;
    color: #fff;
    border: none;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

#app {
    margin-top: 20px;
}

.submitted-data {
    margin-top: 20px;
}
</style>
