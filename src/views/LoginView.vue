<template>
  <form class="login_form" @submit="handleSubmit($event)">
    <div class="form_header">
      <h2>Authorization</h2>
      <h2 class="error_message">{{ status }}</h2>
    </div>
    <label>
      Login
      <input type="text" v-model="login">
    </label>
    <label>
      Password
    <input type="password" v-model="password">
    </label>
    <input type="submit" value="Submit">
  </form>
</template>

<script>
  import axios from 'axios';

  export default {
    data() {
      return {
        login: '',
        password: '',
        status: '',
      }
    },
    methods: {
      navigate() {
        this.$router.push('/profile')
      },
      async handleSubmit(e) {
        e.preventDefault();
        try {
          let res = await axios.post('https://dummyjson.com/auth/login', {
            username: this.login,
            password: this.password,
          })
          if (res.status === 200) {
            localStorage.setItem('token', res.data.token);
            this.status = '';
            this.login='';
            this.password='';
            this.navigate();
          } else {
            this.status = 'Authentification problems'
          }
        }
        catch(e) {
          this.status = 'Invalid Credentials'
        }
      }
    }

  }
</script>

<style>

  .login_form {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
    box-shadow: 0px 2.75px 9px 0px #00000030;
    width: 335px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 20vh;
    margin-bottom: 30vh;
    padding-bottom: 40px;
    border-radius: 10px;
  }
  .form_header {
    display: flex;
    width: 100%;
    padding: 16px;
    justify-content: space-between;
    h2 {
      font-family: 'Roboto', sans-serif;
      font-size: 16px;
      font-weight: 500;
      line-height: 24px;
      letter-spacing: 0.15000000596046448px;
      text-align: left;
    }
  }
  label {
    display: flex;
    flex-direction: column;
    gap: 8px;
    font-family: 'Roboto', sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 20px;
    letter-spacing: 0.25px;
    color: #00000099
  }
  input[type=submit] {
    text-decoration: none;
    border: none;
    background: none;
    cursor: pointer;
    color: #00000099;
  }

  input[type=text], input[type=password] {
    box-shadow: 0px 2.75px 9px 0px #00000030;
    border: none;
    font-family: 'Roboto', sans-serif;
    font-size: 14px;
    padding: 8px;
    width: 152px;
    border-radius: 10px;
  }

  .error_message {
    color:#FF0000;
;
  }
</style>