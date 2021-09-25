<template>
  <li>
    <h2>{{ friend.name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleDetails">{{ showDetails ? 'Hide' : 'Show' }} Details</button>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <ul v-if="showDetails">
      <li><strong>Phone:</strong> {{ friend.phone }}</li>
      <li><strong>Email:</strong> {{ friend.email }}</li>
    </ul>
    <button @click="deleteContact">Delete Contact</button>
  </li>
</template>

<script>
export default {
  /*props: ['friend', 'isFavorite'],*/
  props: {
    name: {
      type: String,
      required: true,
      /*default: 'Test',
      validator: function(value) {
        return value !== null;
      },*/
    },
    friend: {
      name: String,
      phone: String,
      email: String,
    },
    /*isFavorite: String,*/
    isFavorite: {
      // type: String,
      type: Boolean,
      required: false,
      // default: 'Test',
      // validator: function(value) {
      //   return value === '1' || value === '0';
      // },
    },
  },
  // emits: ['toggle-favorite'],
  emits: {
    'toggle-favorite': function(id) {
      if (id) {
        return true;
      } else {
        console.warn('Id is missing!');
        return false;
      }
    },
    'delete-contact': function() { return true },
  },
  data() {
    return {
      showDetails: false,
      // friendIsFavorite: this.isFavorite,
    };
  },
  methods: {
    toggleDetails() {
      this.showDetails = !this.showDetails;
    },
    toggleFavorite() {
      // this.friendIsFavorite = this.friendIsFavorite === '1' ? '0' : '1';
      // this.friendIsFavorite = !this.friendIsFavorite;
      this.$emit('toggle-favorite', this.friend.id);
    },
    deleteContact() {
      this.$emit('delete-contact', this.friend.id);
    },
  }
};
</script>

<style>

</style>