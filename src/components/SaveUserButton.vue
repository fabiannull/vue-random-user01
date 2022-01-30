<template>
  <div>
    <button :disabled="userButtonIsActive" v-on:click="saveUser">
      <font-awesome-icon
        v-bind:class="{ activeButton: userButtonIsActive }"
        class="icon"
        icon="plus"
      />
    </button>
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
    'userButtonIsActive',
  ],
};
</script>

<style scope>
.icon.activeButton {
  color: rgba(84, 88, 102, 0.397);
}
</style>
