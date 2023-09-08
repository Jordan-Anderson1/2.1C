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
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
