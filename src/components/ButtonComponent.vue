<template>
<v-btn
  elevation='2' @click="onPressButton">{{button_name}}</v-btn>
</template>

<script>
export default {
  props: [
    'button_name',
    'onPressButton'
  ],
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    onClickButton () {
      alert('Welcome to your Vue')
    }
  }
}
</script>
