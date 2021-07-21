<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/Lock-With-Key.svg" style="width:200px">
  </div>
  Context <input type="text" v-model="inputtext" autofocus style="margin-right:30px"/>
  AES Key <input type="text" v-model="ekey" />
  <div class="block">
    <div class="algo"><span class="title">SHA1</span> {{ convertSha1()}}</div>
    <div class="algo"><span class="title">SHA256</span> {{ convertSha256()}}</div>
    <div class="algo"><span class="title">MD5</span> {{ convertMd5()}}</div>
    <div class="algo"><span class="title">Base64</span> {{ convertBase64()}}</div>
  </div>
  <hr/>
</template>

<script>
// @ is an alias to /src
import SHA256 from 'crypto-js/sha256';
import MD5 from 'crypto-js/md5';
import Base64 from 'crypto-js/enc-base64';
import UTF8 from 'crypto-js/enc-utf8';
import SHA1 from 'crypto-js/sha1';

export default {
  name: 'Home',
  data() {
    return {
      text: '',
      inputtext: '',
    };
  },
  components: {
  },
  methods: {
    convertSha256() {
      return this.inputtext === '' ? '' : SHA256(this.inputtext).toString();
    },
    convertSha1() {
      return this.inputtext === '' ? '' : SHA1(this.inputtext).toString();
    },
    convertMd5() {
      return this.inputtext === '' ? '' : MD5(this.inputtext).toString();
    },
    convertBase64() {
      return Base64.stringify(UTF8.parse(this.inputtext));
    },
  },
};
</script>

<style scoped>
.title{
  color: black;
  font-weight: 700;
  margin-right: 10px;
}
.algo{
  text-align: left;
  margin: 10px 0;
}
.block{
  width:95%;
  margin:30px auto;
  background-color: darksalmon;
  color: lightgoldenrodyellow;
  font-size: 2rem;
  padding: 10px;
  border-radius: 3px;
}
</style>
