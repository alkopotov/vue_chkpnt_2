<template>
  <main class="content_line">
    <div v-if="user.id" class="profile_wrapper">
      <h1>My Profile</h1>
      <div class="user_info">
        <div class="user_data_list">
          <div class="user_data_item">{{ `Username: ${user.username}` }}</div>
          <div class="user_data_item">{{ `Name: ${user.firstName}` }}</div>
          <div class="user_data_item">{{ `Lastname: ${user.lastName}` }}</div>
          <div class="user_data_item">{{ `Gender: ${user.gender}` }}</div>
          <div class="user_data_item">{{ `Email: ${user.email}` }}</div>
        </div>
        <img :src="user.image" :alt="`${user.lastName} picture`" class="user_picture">
      </div>
    </div>
    <div v-else class="profile_wrapper">
      <h1>{{ status }}</h1>
      <router-link to="/login" v-if="status === 'Authentication Problem'"><button>Authorization</button></router-link>
    </div>
  </main>
</template>

<script>
import axios from 'axios';
import { RouterLink } from 'vue-router';

  export default {
    data() {
      return {
        user: {},
        status: 'Loading...'
      }
    },
    async mounted () {
      try {
        let res = await axios.get('https://dummyjson.com/auth/me', {
          headers: {
            'Authorization' : `Bearer ${localStorage.getItem('token')}`
          }
          });
          if (res.status === 200) {
            this.user = res.data;
          } else {
            this.status = 'Authentication Problem'
          }
      }
      catch(e) {
          this.status = 'Authentication Problem'
      }
    }
  }
</script>

<style>
  .user_info {
    margin-top: 60px;
    display: flex;
    gap: 60px;
  }
  .user_data_list {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .user_picture {
    width: 243px;
    border-radius: 50%;
  }
  .user_data_item {
    font-family: 'Roboto', sans-serif;
    padding: 8px 20px 8px 16px;
    box-shadow: 0px 2.75px 9px 0px #00000030;
    border-radius: 10px;
    font-size: 16px;
    font-weight: 500;
    line-height: 24px;
    letter-spacing: 0.15000000596046448px;
    text-align: left;
  }
  .profile_wrapper {
    max-width: fit-content;
    margin: auto;
    margin-top: 100px;
    min-height: 65vh;
    h1 {
      font-size: 44px;
      font-weight: 700;
      line-height: 60px;
    }
    button {
      align-self: center;
      margin-top: 50px;
      background: #FF6464;
      color: white;
      font-size: 20px;
      font-weight: 500;
      line-height: 29px;
      letter-spacing: 0px;
      text-align: left;
      border: none;
      width: 208px;
      height: 43px;
      text-align: center;
      cursor: pointer;
    }
  }
</style>