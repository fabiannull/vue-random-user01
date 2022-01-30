<template>
  <div id="app">
    <ProfileCard
      v-bind:userFirstName="userFirstName"
      v-bind:userLastName="userLastName"
      v-bind:userAge="userAge"
      v-bind:userCity="userCity"
      v-bind:userCountry="userCountry"
      v-bind:userPicture="userPicture"
      v-bind:userMailAdress="userMailAdress"
    ></ProfileCard>
    <div class="buttonSection">
      <GenerateUserButton
        v-bind:loadingState="loadingState"
      ></GenerateUserButton>

      <SaveUserButton
        v-bind:userFirstName="userFirstName"
        v-bind:userLastName="userLastName"
        v-bind:userAge="userAge"
        v-bind:userCity="userCity"
        v-bind:userCountry="userCountry"
        v-bind:userPicture="userPicture"
        v-bind:userMailAdress="userMailAdress"
        v-bind:savedUser="savedUser"
        @saveUser="saveUser"
      ></SaveUserButton>
    </div>
    <SavedUserList
      v-bind:savedUser="savedUser"
      @deleteUser="deleteUser"
    ></SavedUserList>
  </div>
</template>

<script>
import ProfileCard from './components/ProfileCard.vue';
import GenerateUserButton from './components/GenerateUserButton.vue';
import SaveUserButton from './components/SaveUserButton.vue';
import SavedUserList from './components/SavedUserList.vue';

export default {
  name: 'App',
  components: {
    ProfileCard,
    GenerateUserButton,
    SaveUserButton,
    SavedUserList,
  },
  data: () => ({
    loadingState: false,
    userFirstName: '',
    userLastName: '',
    userAge: '',
    userCity: '',
    userCountry: '',
    userPicture: '',
    userMailAdress: '',
    savedUser: [],
  }),
  methods: {
    async loadUser () {
      this.loadingState = true;

      let apiUrl = 'https://randomuser.me/api/';

      try {
        let response = await this.axios.get(apiUrl);
        this.items = response;
        this.userFirstName = response.data.results[0].name.first;
        this.userLastName = response.data.results[0].name.last;
        this.userAge = response.data.results[0].dob.age;
        this.userCity = response.data.results[0].location.city;
        this.userCountry = response.data.results[0].location.country;
        this.userPicture = response.data.results[0].picture.large;
        this.userMailAdress = response.data.results[0].email;
      } catch (e) {
        console.log(e);
      }
      this.loadingState = false;
    },
    saveUser (newUserObject) {
      this.savedUser = [...this.savedUser, newUserObject];
    },
    deleteUser (userID) {
      this.savedUser = this.savedUser.filter(user => user.id !== userID);
    },
  },
  created () {
    this.loadUser();
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Kumbh Sans', sans-serif;
}

body {
  background-color: rgb(60, 199, 209);
}

.buttonSection {
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>
