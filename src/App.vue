<template>
  <div id="app">
    <Header />
    <b-container class="bv-example-row">
      <b-row>
        <b-col cols= "4">
          <ContactForm v-on:add-contact="addContact"/>
        </b-col>
        <b-col cols= "8">
          <Find v-bind:contacts="contacts" v-on:del-contact="deleteContact"/>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script> 
import Header from './components/layouts/Header';
import ContactForm from './components/ContactForm';
import Find from './components/Find';

export default {
  name: 'App',
  components: {
    Header,
    ContactForm,
    Find
  },
  data() {
    return {
      contacts: [],
    };
  },
  methods: {
    deleteContact(id) {
      alert("Are you sure?");
      this.contacts = this.contacts.filter((contact) => contact.id !== id);
    },
    addContact(newContact) {
      this.contacts = [...this.contacts, newContact];
    },
  },
};
</script>

<style>
  h3 {
    text-align: center;
  }

  ul {
    list-style-type: none;
  }
</style>
