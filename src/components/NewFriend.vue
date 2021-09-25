<template>
  <section class="card">
    <h2>New Friend</h2>
    <form @submit.prevent="addFriend">
<!--      <div>-->
<!--        <label for="id">Id:</label>-->
<!--        <input type="text" id="id" v-model="newFriend.id">-->
<!--      </div>-->
      <div>
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="newFriend.name">
      </div>
      <div>
        <label for="phone">Phone:</label>
        <input type="tel" id="phone" v-model="newFriend.phone">
      </div>
      <div>
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="newFriend.email">
      </div>
      <div>
        <label for="favorite">Is Favorite?</label>
        <input type="checkbox" id="favorite" v-model="newFriend.isFavorite">
      </div>

      <button>Add new friend</button>
<!--      <button @click.prevent="addFriend">Add new friend</button>-->
    </form>
  </section>
</template>

<script>
export default {
  emits: {
    'add-friend': function({ name, phone, email }) {
      if (!name || name === '') {
        alert('Name is missing!');
        return false;
      } else if (!phone || phone === '') {
        alert('Phone is missing!');
        return false;
      } else if (!email || email === '') {
        alert('Email is missing!');
        return false;
      } else {
        return true;
      }
    }
  },
  data() {
    return {
      newFriend: {
        id: '',
        name: '',
        phone: '',
        email: '',
        isFavorite: false,
      }
    }
  },
  methods: {
    addFriend() {
      this.$emit('add-friend', {
        ...this.newFriend,
        id: new Date().toISOString(),
      });
      this.clear();
    },
    clear() {
      this.newFriend = {
        id: '',
        name: '',
        phone: '',
        email: '',
        isFavorite: false,
      }
    }
  },
}
</script>