<template>
  <div>
    <app-header v-bind:propsdata = "str"
    v-on:renew="renewStr"
    ></app-header>
    <h2>{{ propsdata }}</h2>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';

export default {
  data: function() {
    return {
      str: 'hi' 
    } // component 재활용 시, 참조오류를 방지하기 위해서 함수로 새 객체를 return 해주는 방식을 작성 필요. 
  },  
  components: {
    'app-header': AppHeader
  },
  methods: {
    renewStr: function() {
      this.str = 'Hello Hello Hello How low';
    }
  }
}
</script>

<style>

</style>

// component 이름은 기본 tag와의 구별을 위해 두 단어 이상의 PascalCase로 작성해준다. 