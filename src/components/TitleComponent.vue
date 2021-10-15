<template>
  <div>
    <h1><strong>{{title}}</strong></h1>
      <small class="red--text h-25">{{error_message}}</small>
    <h2 class="mt-2"><strong>{{sub_title}}</strong></h2>
  </div>
</template>

<script>
export default {
  props: [
    'title',
    'sub_title',
    'error_message'
  ],
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>
