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

    <GenerateUserButton v-bind:loadingState="loadingState"></GenerateUserButton>
  </div>
</template>

<script>
import ProfileCard from './components/ProfileCard.vue';
import GenerateUserButton from './components/GenerateUserButton.vue';

export default {
  name: 'App',
  components: { ProfileCard, GenerateUserButton },
  data: () => ({
    loadingState: false,
    items: [],
    userFirstName: '',
    userLastName: '',
    userAge: '',
    userCity: '',
    userCountry: '',
    userPicture: '',
    userMailAdress: '',
  }),
  methods: {
    async loadUser () {
      this.loadingState = true;
      //console.log('button geht')
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
        //console.log(response)
      } catch (e) {
        console.log(e);
      }
      this.loadingState = false;
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
  background-color: rgb(24, 161, 175);
}
</style>
