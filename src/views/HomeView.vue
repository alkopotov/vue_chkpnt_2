<script>
  import {RouterLink} from 'vue-router'
</script>

<template>
  <div class="wrapper">
  <main class="home_page_wrapper content_line">
    <div>
      <h1>Home page</h1>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium recusandae minus eos eius error vel, velit, quasi quisquam sequi dolore corporis totam earum ea facere minima amet laborum cumque ipsum.</p>
      <router-link to="/login"><button>Authorization</button></router-link>
    </div>
    <img src="../assets/images/home_pict.png" alt="">
  </main>
</div>
</template>

<style>
  .home_page_wrapper {
    margin-top: 100px;
    display: flex;
    justify-content: space-between;
    div {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    img {
      width: 301px;
    }
    button {
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
    p{
      max-width: 500px;
      font-size: 16px;
      font-weight: 400;
      line-height: 24px;
    }
  }
  .wrapper {
    min-height: 70vh;
  }

</style>