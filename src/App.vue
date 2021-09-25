<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <new-friend @add-friend="addFriend"></new-friend>
    <ul>
      <friend-contact v-for="friend in friends" :key="friend.id" :friend="friend"
        :is-favorite="friend.isFavorite" :name="friend.name"
        @toggle-favorite="toggleFavorite"
        @delete-contact="deleteFriend"></friend-contact>
<!--      <friend-contact :key="friends[0].id" :friend="friends[0]"
        :isFavorite="'5'" :name="friends[0].name"></friend-contact>-->
    </ul>
  </section>
</template>

<script>
import FriendContact from './components/FriendContact';
import NewFriend from './components/NewFriend';

export default {
  components: {NewFriend, FriendContact},
  data() {
    return {
      friends: [
        {
          id: 'camilo0',
          name: 'Camilo Guerra',
          phone: '0123 45678 90',
          email: 'camilo0@localhost.com',
          isFavorite: true,
        },
        {
          id: 'luisa0',
          name: 'Luisa Barrera',
          phone: '0987 65432 10',
          email: 'luisa0@localhost.com',
          isFavorite: false,
        },
      ]
    }
  },
  methods: {
    toggleFavorite(id) {
      // const indexSelectedFriend = this.friends.findIndex(friend => friend.id === id);
      // console.log(id, indexSelectedFriend);
      // if (indexSelectedFriend >= 0) {
      //   this.friends[indexSelectedFriend].isFavorite = !this.friends[indexSelectedFriend].isFavorite;
      // }
      const selectedFriend = this.friends.find(friend => friend.id === id);
      selectedFriend.isFavorite = !selectedFriend.isFavorite;
    },
    addFriend(newFriend) {
      this.friends.push(newFriend);
    },
    deleteFriend(id) {
      this.friends = this.friends.filter(friend => friend.id !== id);
    }
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}

.card {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
</style>