<template>
  <div>
    <img v-bind:src="userPicture" alt="Picture of Random User" />
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
    'userPicture'
  ]
}
</script>

<style></style>
