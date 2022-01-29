<template>
  <div>
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

<style scope></style>
