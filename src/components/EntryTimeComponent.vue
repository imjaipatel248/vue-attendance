<template>
<div>
    <h3 class="my-4"><strong>{{msg}}</strong></h3>
  <div v-bind:key="entry_time.key" v-for="entry_time  in entry_times">
    <div class="mt-2" >{{entry_time.name}}</div>
  </div>
</div>
</template>

<script>
export default {
  props: ['entry_times'],
  data () {
    return {
      msg: 'Entry Time'
    }
  }
}
</script>
