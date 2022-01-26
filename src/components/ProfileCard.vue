<template>
  <div class="profileCard">
    <div>
      <img class="upperPattern" src="../assets/bg-pattern-card.svg" alt="" />
    </div>
    <div class="content">
      <img
        class="profilePic"
        v-bind:src="userPicture"
        alt="Picture of Random User"
      />
      <h1>
        {{ userFirstName }} {{ userLastName }} <span>{{ userAge }}</span>
      </h1>
      <h2>{{ userCity }} {{ userCountry }}</h2>
      <h2 class="mailContent">{{ userMailAdress }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProfileCard',
  components: {},
  data: () => ({}),

  props: [
    'userFirstName',
    'userLastName',
    'userAge',
    'userCity',
    'userCountry',
    'userPicture',
    'userMailAdress',
  ],
};
</script>

<style scope>
.profileCard {
  max-width: 375px;
  width: 90%;
  margin: auto;
  background-color: whitesmoke;
  border-radius: 20px 20px 20px 20px;
}

.upperPattern {
  width: 100%;
  display: block;
  border-radius: 20px 20px 0px 0px;
}

.profilePic {
  border-radius: 50%;
  border: 5px solid whitesmoke;
  margin-top: -70px;
  transition: transform 1s;
}

.profilePic:hover {
  transform: scale(1.1);
}

.content {
  text-align: center;
}

h1 {
  font-weight: 700;
  font-size: 1.7rem;
  color: rgb(45, 50, 72);
  margin-top: 1rem;
}

h1 span {
  color: rgb(106, 111, 129);
  font-weight: 400;
  margin-left: 0.5rem;
}

h2 {
  color: rgb(106, 111, 129);
  margin-top: 0.6rem;
  margin-bottom: 1.7rem;
  font-weight: 400;
  font-size: 1rem;
}

.mailContent {
  padding-top: 1.5rem;
  padding-bottom: 1.5rem;
  border-top: rgb(106, 111, 129) 1px solid;
}

.content,
.mailContent {
  border-radius: 0px 0px 20px 20px;
}
</style>
