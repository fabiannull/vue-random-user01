<template>
  <div class="savedUser">
    <img v-bind:src="user.userPicture" alt="" />

    <font-awesome-icon
      class="icon"
      icon="trash-alt"
      @click="$emit('deleteUser', user.id)"
    />
  </div>
</template>

<script>
export default {
  name: 'SavedUser',
  components: {},
  data: () => ({}),
  methods: {},
  computed: {},

  props: ['user'],
};
</script>

<style scope>
.savedUser {
  margin-top: 1.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 150%;

  color: rgb(84, 88, 102);
  cursor: pointer;
}
.savedUser img {
  border-radius: 50%;
  border: 5px solid whitesmoke;

  transition: transform 1s;
}

.savedUser img:hover {
  transform: scale(1.1);
}

.icon {
  margin-top: 10%;
}
</style>
