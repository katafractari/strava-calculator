<template>
  <b-container>
    <b-form @submit="onSubmit">
      <b-row class="mb-3">
        <b-col>
          <b-form-input v-model="form.athlete1"
                        type="text"
                        placeholder="Athlete 1 Username">
          </b-form-input>
        </b-col>
        <b-col>
          <b-form-input v-model="form.athlete2"
                        type="text"
                        placeholder="Athlete 2 Username">
          </b-form-input>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <b-button type="submit" variant="primary">
            Compare climbing abilities
          </b-button>
        </b-col>
      </b-row>
    </b-form>
  </b-container>
</template>

<script>
import strava from 'strava-v3'

export default {
  name: 'HelloWorld',
  data () {
    return {
      form: {
        athlete1: '',
        athlete2: ''
      }
    }
  },
  methods: {
    onSubmit () {
      strava.athlete.get({ access_token: '47e840fcf533a908b19e93f6a516afc9b51c4ed8', id: 15573391 }, (err, payload) => {
        if (!err) {
          console.log(payload);
        } else {
          console.log(err);
        }
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
