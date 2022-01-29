<template>
  <div>
    <button v-on:click="saveUser">
      <font-awesome-icon class="icon" icon="plus" />
    </button>
    {{ userIDList }}
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'SaveUserButton',
  components: {},
  data: () => ({
    userIDList: [],
  }),
  methods: {
    saveUser () {
      for (var userData of this.savedUser) {
        console.log(userData.id);
      }

      const newUserObject = {
        id: uuidv4(),
        userFirstName: this.userFirstName,
        userLastName: this.userLastName,
        userAge: this.userAge,
        userCity: this.userCity,
        userCountry: this.userCountry,
        userPicture: this.userPicture,
        userMailAdress: this.userMailAdress,
        userShow: false,
      };

      this.$emit('saveUser', newUserObject);
    },
  },

  props: [
    'userFirstName',
    'userLastName',
    'userAge',
    'userCity',
    'userCountry',
    'userPicture',
    'userMailAdress',
    'savedUser',
  ],
};
</script>

<style scope></style>
