<template>
  <div class="mw6 center pa3 sans-serif">
            <h1 class="mb4">Contacts</h1>
            <p v-if = "state == 'error'" class = "orange">{{ error }}</p>
            <div v-else-if = "state == 'ready'">
                <contact v-for="contact in contacts" :key="contact.id" :contact="contact" /> 
            </div>
            <p v-if-else="state == 'loading'">Loading contact...</p>
            <div class="pa2 mb3 striped--near-white">
                <header class="b mb2">Name</header>
                <div class="pl2">
                    <p class="mb2">Phone</p>
                    <p class="pre mb3">Address</p>
                    <p class="mb2">Email</p>
                </div>
            </div>
        </div>
</template>

<script>

import Contact from "@components/Contact.vue";
export default {
  name: 'App',
  components: {
    Contact
  },
    data() {
      return {
        contacts: [],
        error: "",
        state: "loading"
    }
  },
  created() {
    this.loadContacts()
  },
  methods: {
    async loadContacts() {
      try {
        const contacts = await fetch("http://localhost:3000/contacts");
        this.contacts = contacts.json();
        this.state = 'ready';
      } catch (err) {
        this.error = err;
        this.state = 'error';

      }
    }
  }
};
</script>

