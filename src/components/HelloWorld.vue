<template>
  <div class="hello">
    <form action>
      <input type="text" placeholder="text" v-model="text">
      <input type="submit" value="decide" v-on:click="submitClick">
    </form>
  </div>
</template>

<script>/* eslint-disable */
  import Axios from "axios";
  export default {
    name: "HelloWorld",
    data() {
      return {
        text: null
      };
    },
    methods: {
      submitClick() {
        const body = {
          type: String,
          required: true,
          text: this.text
        };
        axios.get(`http://localhost:3000/hoge/${this.text}`)
        .then(res => {
          console.log(res.data.name)
        })
        .catch(err => {
          console.error(err)
        });
      }
    }
  };
</script>
