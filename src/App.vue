<template>
  <section>
    <header>
      <h1>My friends </h1>
    </header>
    <new-friend @add-friend="addFriend"></new-friend>
    <ul>
      <friend-contact v-for="friend in friends" :key="friend.id" 
        :id="friend.id"
        :name="friend.name" 
        :phone-number="friend.phone"
        :email-address="friend.email"
        :is-favorite="friend.isFavorite"
        @toggle-favorite="toggleFavoritesState"
      >
      </friend-contact>
      
      
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        { id: 'manuel', name: 'Manuel', phone: '123456', email: 'aaa@aaa.com',isFavorite:false },
        { id: 'julie', name: 'Julie', phone: '987654', email: 'bbbb@bbb.com',isFavorite:false },
        { id: 'max', name: 'Max', phone: '456789', email: 'cccc@cccc.com',isFavorite:true },
      ]
    };
  },
  methods:{
    toggleFavoritesState(id){
      // const friendIndex=this.friends.findIndex((friend)=>{
      //   return friend.name===friendName;
      // });
      // this.friends[friendIndex].isFavorite=!this.friends[friendIndex].isFavorite;
      console.log('Toggling favorite id:',id);
      const tmpFriend=this.friends.find((friend)=>{
        return friend.id===id;
      });
      tmpFriend.isFavorite=!tmpFriend.isFavorite;
    },
    addFriend(nameTmp,phoneTmp,emailTmp){
      const newFriend={
        id:nameTmp,
        name:nameTmp,
        phone:phoneTmp,
        email:emailTmp,
        isFavorite:false
      }
      this.friends.push(newFriend);
      console.log('Adding new friend:',newFriend);
    }
  } 
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

#app li,
#app form {
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
</style>
