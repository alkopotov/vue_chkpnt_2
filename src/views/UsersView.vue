<template>
  <div class="user_list">
    <div v-if="users.length === 0">Loading...</div>
    <div v-for="user in users" :key="user.id" class="user_item">
      <div class="user_fullname">
        {{ `${user.firstName} ${user.lastName} ${user.maidenName}`}}
      </div>
      <div class="user_email">
        {{ user.email }}
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    data() {
      return {
        users: [
        ]
      }
    },
    async mounted() {
      try {
        let res = await axios.get('https://dummyjson.com/users')
        this.users = res.data.users;
      }
      catch(e) {
        console.log(e);
      }
    }
  }

</script>

<style>
  .user_list {
    display: grid;
    width: fit-content;
    gap: 18px;
    margin-top: 80px;
    margin-left: auto;
    margin-right: auto;
  }

  .user_item {
    display: flex;
    gap: 50px;
    justify-content: space-between;
    padding: 16px;
    box-shadow: 0px 2.75px 9px 0px #00000030;
    border-radius: 10px;
  }
  
  .user_fullname {
    font-family: 'Roboto', sans-serif;
    font-size: 16px;
    font-weight: 500;
    line-height: 24px;
    letter-spacing: 0.15000000596046448px;
    text-align: left;
  }

  .user_email {
    font-family: 'Roboto', sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 20px;
    letter-spacing: 0.25px;
    color: #00000099;
  }

</style>