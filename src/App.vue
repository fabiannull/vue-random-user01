<template>
  <div id="app">
    <div class="lds-default" v-if="loadingState == true">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
    <button v-else v-on:click="loadUser">User anfordern</button>

    <hr />
    <ProfileCard
      v-bind:userFirstName="userFirstName"
      v-bind:userLastName="userLastName"
      v-bind:userAge="userAge"
      v-bind:userCity="userCity"
      v-bind:userCountry="userCountry"
      v-bind:userPicture="userPicture"
    ></ProfileCard>
  </div>
</template>

<script>
import ProfileCard from './components/ProfileCard.vue'

export default {
  name: 'App',
  components: { ProfileCard },
  data: () => ({
    loadingState: false,
    items: [],
    userFirstName: '',
    userLastName: '',
    userAge: '',
    userCity: '',
    userCountry: '',
    userPicture: ''
  }),
  methods: {
    async loadUser () {
      this.loadingState = true
      //console.log('button geht')
      let apiUrl = 'https://randomuser.me/api/'

      try {
        let response = await this.axios.get(apiUrl)
        this.items = response
        this.userFirstName = response.data.results[0].name.first
        this.userLastName = response.data.results[0].name.last
        this.userAge = response.data.results[0].dob.age
        this.userCity = response.data.results[0].location.city
        this.userCountry = response.data.results[0].location.country
        this.userPicture = response.data.results[0].picture.large
        //console.log(response)
      } catch (e) {
        console.log(e)
      }
      this.loadingState = false
    }
  },
  created () {
    this.loadUser()
  }
}
</script>

<style>
.lds-default {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-default div {
  position: absolute;
  width: 6px;
  height: 6px;
  background: rgb(30, 27, 77);
  border-radius: 50%;
  animation: lds-default 1.2s linear infinite;
}
.lds-default div:nth-child(1) {
  animation-delay: 0s;
  top: 37px;
  left: 66px;
}
.lds-default div:nth-child(2) {
  animation-delay: -0.1s;
  top: 22px;
  left: 62px;
}
.lds-default div:nth-child(3) {
  animation-delay: -0.2s;
  top: 11px;
  left: 52px;
}
.lds-default div:nth-child(4) {
  animation-delay: -0.3s;
  top: 7px;
  left: 37px;
}
.lds-default div:nth-child(5) {
  animation-delay: -0.4s;
  top: 11px;
  left: 22px;
}
.lds-default div:nth-child(6) {
  animation-delay: -0.5s;
  top: 22px;
  left: 11px;
}
.lds-default div:nth-child(7) {
  animation-delay: -0.6s;
  top: 37px;
  left: 7px;
}
.lds-default div:nth-child(8) {
  animation-delay: -0.7s;
  top: 52px;
  left: 11px;
}
.lds-default div:nth-child(9) {
  animation-delay: -0.8s;
  top: 62px;
  left: 22px;
}
.lds-default div:nth-child(10) {
  animation-delay: -0.9s;
  top: 66px;
  left: 37px;
}
.lds-default div:nth-child(11) {
  animation-delay: -1s;
  top: 62px;
  left: 52px;
}
.lds-default div:nth-child(12) {
  animation-delay: -1.1s;
  top: 52px;
  left: 62px;
}
@keyframes lds-default {
  0%,
  20%,
  80%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.5);
  }
}
</style>
