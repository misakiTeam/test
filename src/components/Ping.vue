<template>
  <div>
    <p>{{ msg }}</p>
    <div class='btn btn-primary'>{{msg}}</div>
  </div>
</template>

<script type="module">
import axios from 'axios';

export default {
  name: 'Ping',
  data() {
    return {
      msg: ''
    };
  },
  methods: {
    getMessage() {
      const path = 'http://localhost:5000/ping';
      axios
        .get(path)
        .then(res => {
          this.msg = res.data;
        })
        .catch(error => {
          console.error(error);
        });
    }
  },
  created() {
    this.getMessage();
  }
};
</script>
