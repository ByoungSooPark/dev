<template>
  <div>
    <button type=”button” name=”button” @click='getUsers'>get users</button>
    <table>
      <th>url</th>
      <th>email</th>
      <th>staff</th>
      <tbody>
      <tr v-for="elem in users" :key="elem.key">
        <td><a :href="elem.url">{{ elem.username }}</a></td>
        <td>{{ elem.email }}</td>
        <td>{{ elem.is_staff }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      users: []
    }
  },
  methods: {
    getUsers() {
      axios.get('http:/127.0.0.1:8000/users/')
        .then(res => this.users=res.data)
        .catch(error => console.log(error))
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
