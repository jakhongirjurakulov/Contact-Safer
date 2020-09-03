<template>
  <div class="find">
    <h3>
      <b-icon-list></b-icon-list>List of Contacts
    </h3>
    <input
      id="bd-search-input"
      type="search"
      placeholder="Search..."
      autocomplete="off"
      aria-label="Search docs"
      class="form-control ds-input mt-4 ml-5"
      spellcheck="false"
      role="combobox"
      aria-autocomplete="list"
      aria-expanded="false"
      aria-owns="algolia-autocomplete-listbox-0"
      dir="auto"
      style="position: relative; vertical-align: top;"
    />
    <!-- v-model="searchContacts" -->

    <!--Поиск контактов-->
    <!-- <b-container>
      <b-row>
        <b-col cols="8">
          <ul>
            <li variant="primary" class="ml-5" v-for="item in contacts" v-bind:key="item.id">
              <b-card
                header-tag="header"
                footer-tag="footer"
                class="d-flex justify-content-center mt-2"
              >
                <b-card-text><b>Name:</b> <em>{{ item.name }}</em></b-card-text>
                <b-card-text><b>Phone Number:</b>(+998) <br><em>{{ item.phoneNumber }} <br> {{ item.phoneNumberAdd}}</em></b-card-text>
                <b-card-text><b>Address:</b> <em>{{ item.address }} <br> {{ item.addressAdd}}</em></b-card-text>
                <b-card-text><b>E-mail:</b> <em>{{ item.email }} <br> {{ item.emailAdd}}</em></b-card-text>
                <b-button variant="info" class="ml-5">Edit</b-button>
                <b-button
                  variant="danger"
                  class="ml-5"
                  @click="$emit('del-contact', contact.id)"
                >Delete</b-button>
              </b-card>
            </li>
          </ul>
        </b-col>
      </b-row>
    </b-container>
    -->

    <div v-bind:key="contact.id" v-for="contact in contacts">
      <FindContact v-bind:contact="contact" v-on:del-contact="$emit('del-contact', contact.id)" />
    </div>
  </div>
</template>

<script>
import FindContact from "./FindContact";
export default {
  components: {
    FindContact,
  },
  props: ["contacts"],
  /*------ Поиск контактов ------*/
  /* data() {
    return {
      searchContacts: '',
    };
  },
  computed: {
    resultList() {
      --------------------1st way---------------------
      if(this.searchContacts){
      return this.contacts.filter((c)=>{
        return c.name.match(/^this.searchContacts/g);
      })
      } else {
        return this.contacts;
      }
      --------------------2nd way---------------------
      if(this.searchContacts){
      return this.contacts.filter((c)=>{
        return c.name.includes(this.searchContacts);
      })
      } else {
        return this.contacts;
      }
    },
  }, */
};
</script>

<style scoped>
</style>
