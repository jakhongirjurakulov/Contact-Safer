<template>
  <main class="mt-2 main">
    <b-container class="bv-example-row">
      <b-row>
        <b-col cols="8">
          <ul>
            <li variant="primary" class="ml-5">
              <b-card
                header-tag="header"
                footer-tag="footer"
                class="d-flex justify-content-center mt-2"
              >
                <b-card-text
                  ><b>Name:</b> <em>{{ contact.name }}</em></b-card-text
                >
                <b-card-text
                  ><b>Phone Number:</b>+998 <br /><em
                    >{{ contact.phoneNumber }} <br />
                    {{ contact.phoneNumberAdd }}</em
                  ></b-card-text
                >
                <b-card-text
                  ><b>Address:</b>
                  <em
                    >{{ contact.address }} <br />
                    {{ contact.addressAdd }}</em
                  ></b-card-text
                >
                <b-card-text
                  ><b>E-mail:</b>
                  <em
                    >{{ contact.email }} <br />
                    {{ contact.emailAdd }}</em
                  ></b-card-text
                >
                <b-button variant="info" class="ml-5">Edit</b-button>
                <b-button
                  variant="danger"
                  class="ml-5"
                  @click="$emit('del-contact', contact.id)"
                  >Delete</b-button
                >
              </b-card>
            </li>
          </ul>
        </b-col>
      </b-row>
    </b-container>
  </main>
</template>

<script>
export default {
  props: ['contact'],
};
</script>

<style scoped>
.card {
  box-shadow: rgba(0, 0, 0, 0.117647) 0px 1px 6px,
    rgba(0, 0, 0, 0.117647) 0px 1px 4px;
}
</style>
