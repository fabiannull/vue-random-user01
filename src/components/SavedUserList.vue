<template>
  <div>
    <ul>
      <li v-for="user in savedUser" v-bind:key="user.id">
        <SavedUser
          v-bind:user="user"
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

<style scope></style>
