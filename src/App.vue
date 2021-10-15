<template>
  <v-app id="inspire">
    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col>
            <v-sheet
              min-height="90vh"
              rounded="lg"
            >
              <div id='app'>
                <div>
                  <div>
                      <TitleComponent :title="app_title" :sub_title="sub_title" :error_message="error_message"/>
                  </div>
                  <div class="mt-2">
                      <ButtonComponent button_name="-" :onPressButton='decrement'/>
                          <span class="mx-2">{{count}}</span>
                      <ButtonComponent button_name="+" :onPressButton='increment'/>
                  </div>
                  <h4>{{text}}</h4>
                  <div>
                    <EntryTimeComponent :entry_times="entry_times" />
                  </div>
                </div>
              </div>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>

</template>

<script>
import ButtonComponent from './components/ButtonComponent'
import TitleComponent from './components/TitleComponent'
import EntryTimeComponent from './components/EntryTimeComponent'
export default {
  name: 'App',
  data () {
    return {
      app_title: 'THE BAY',
      sub_title: 'Entry Control',
      error_message: '',
      count: 0,
      entry_times: [],
      text: 'People Shopping'
    }
  },
  components: {
    ButtonComponent,
    TitleComponent,
    EntryTimeComponent
  },
  methods: {
    increment () {
      if (this.count === 20) {
        this.error_message = "Number of people can't exceeds 20"
        return
      } else {
        this.error_message = ''
      }
      this.count += 1
      const obj = {
        key: Math.random(),
        name: 'Entered at ' + this.getCurrentTime()}
      this.entry_times.unshift(obj)
    },
    decrement () {
      if (this.count === 0) {
        this.error_message = 'Can not have people less then 0'
        return
      } else {
        this.error_message = ''
      }
      this.count -= 1
      const obj = {
        key: Math.random(),
        name: 'Exited at ' + this.getCurrentTime()}
      this.entry_times.unshift(obj)
    },
    getCurrentTime () {
      var time = new Date()
      return ('0' + time.getHours()).slice(-2) + ':' +
    ('0' + time.getMinutes()).slice(-2) + ':' +
    ('0' + time.getSeconds()).slice(-2)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
