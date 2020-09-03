<template>
  <div>
    <b-row>
      <h3><b-icon-person-plus-fill></b-icon-person-plus-fill>Add Contact</h3>
    </b-row>
    <form @submit="addContact">
      <b-row>
        <b-col cols="12">
          <label for="name">Name:</label>
          <br />
        </b-col>

        <b-col cols="10">
          <b-form-input
            v-model="name"
            name="name"
            placeholder="Enter name"
            class="name"
          ></b-form-input>
        </b-col>

        <b-col cols="2">
          <b-button variant="outline-primary" @click="contactFilter"
            >+</b-button
          >
        </b-col>
      </b-row>

      <b-row>
        <b-col cols="12">
          <label for="number">Telephone Number:</label>
          <br />
        </b-col>

        <b-col cols="10">
          <b-form-input
            v-model="phoneNumber"
            name="phoneNumber"
            placeholder="(+998)"
            id="number"
          ></b-form-input>
        </b-col>

        <b-container v-bind:class="{ active: isActive }">
          <b-row class="mt-2">
            <b-col cols="10">
              <b-form-input
                v-model="phoneNumberAdd"
                name="phoneNumberAdd"
                placeholder="(+998)"
                id="phoneNumberAdd"
              ></b-form-input>
            </b-col>
          </b-row>
        </b-container>
        <!-- <ContactFormPhoneNum v-bind:class="{ active: isActive }" /> -->
      </b-row>

      <b-row>
        <b-col cols="12">
          <label for="address">Address:</label>
          <br />
        </b-col>

        <b-col cols="10">
          <b-form-input
            v-model="address"
            name="address"
            placeholder="Enter address"
            id="address"
          ></b-form-input>
        </b-col>

        <b-container v-bind:class="{ active: isActive }">
          <b-row class="mt-2">
            <b-col cols="10">
              <b-form-input
                v-model="addressAdd"
                name="addressAdd"
                placeholder="Enter address"
                id="addressAdd"
              ></b-form-input>
            </b-col>
          </b-row>
        </b-container>
        <!-- <ContactFormAddress v-bind:class="{ active: isActive }" /> -->
      </b-row>

      <b-row>
        <b-col cols="12">
          <label for="e-mail">E-mail:</label>
          <br />
        </b-col>

        <b-col cols="10">
          <b-form-input
            v-model="email"
            name="email"
            placeholder="Enter e-mail"
            id="e-mail"
          ></b-form-input>
        </b-col>

        <b-container v-bind:class="{ active: isActive }" >
          <b-row class="mt-2">
            <b-col cols="10">
              <b-form-input
                v-model="emailAdd"
                name="emailAdd"
                placeholder="Enter e-mail"
                id="emailAdd"
              ></b-form-input>
            </b-col>
          </b-row>
        </b-container>
        <!-- <ContactFormEmail v-bind:class="{ active: isActive }" /> -->
      </b-row>

      <b-row>
        <b-col cols="12" class="d-flex justify-content-center">
          <input
            type="submit"
            :disabled="name === '' && phoneNumber === ''"
            class="btn btn-primary mt-3"
            value="Add"
          />
        </b-col>
      </b-row>
    </form>
  </div>
</template>

<script>
import uuid from 'uuid';
export default {
  props: ['contacts'],
  components: {
    /* ContactFormPhoneNum,
    ContactFormAddress,
    ContactFormEmail, */
  },
  data() {
    return {
      name: '',
      phoneNumber: '',
      phoneNumberAdd: '',
      address: '',
      addressAdd: '',
      email: '',
      emailAdd: '',
      isActive: true,
    };
  },
  methods: {
    addContact(e) {
      e.preventDefault();
      const newContact = {
        id: uuid,
        name: this.name,
        nameAdd: this.nameAdd,
        phoneNumber: this.phoneNumber,
        phoneNumberAdd: this.phoneNumberAdd,
        address: this.address,
        addressAdd: this.addressAdd,
        email: this.email,
        emailAdd: this.emailAdd,
      };
      // Send up to parent
      this.$emit('add-contact', newContact);
      this.name = '';
      this.nameAdd = '';
      this.phoneNumber = '';
      this.phoneNumberAdd = '';
      this.address = '';
      this.addressAdd = '';
      this.email = '';
      this.emailAdd = '';
    },
    contactFilter() {
      this.isActive = !this.isActive;
      // some code to filter users
    },
  },
};
</script>

<style scoped>
.active {
  display: none;
}
</style>
