<template>
  <!-- form tag는 정보를 제출하고 새로운 페이지로 넘어가는 기능이 있어 새로고침 현상이 있으며, 하기 preventDefault로 막아줌-->
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit" >login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return { // 컴포넌트 간 데이터 공유가 이뤄지지 않게 하기 위해 새로운 객체 리턴
      username: '',
      password: ''
    }
  },
  methods: {
    submitForm: function() {
      // event.preventDefault(); // 새로고침 방지 -> vue.js에서 해당 기능 제공 
      console.log(this.username, this.password);
      let url = 'https://jsonplaceholder.typicode.com/users';
      let data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
        .then(res => {
          console.log(res);
        })
        .catch(err => console.log(err))
    } 
  }
}
</script>

<style>

</style>