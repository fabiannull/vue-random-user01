<template>
  <div class="userList">
    <ul>
      <li v-for="user in savedUser" v-bind:key="user.id">
        <SavedUser
          v-bind:user="user"
          v-bind:userID="user.id"
          v-bind:savedUser="savedUser"
          @selectedUser="$emit('selectedUser', user.id)"
          @deleteUser="$emit('deleteUser', user.id)"
        ></SavedUser>
      </li>
    </ul>
  </div>
</template>

<script>
import SavedUser from './SavedUser.vue';

export default {
  name: 'SavedUserList',
  components: { SavedUser },
  data: () => ({}),
  methods: {},
  computed: {},

  props: ['savedUser'],
};
</script>

<style scope>
.userList {
  width: 100%;
  display: flex;
  justify-content: center;
}

ul {
  list-style: none;
  width: 80%;
  display: flex;
  justify-content: space-evenly;
}

ul > li {
  display: inline-block;
}
</style>
