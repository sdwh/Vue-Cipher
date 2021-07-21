<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/Lock-With-Key.svg" style="width:200px">
  </div>
  <div class="input-block">
  Context <input type="text" class="input-text"
    v-model="inputtext" autofocus/>
  </div>
  <div class="block">
    <div class="algo">
      <span class="title">SHA1</span>
      <span class="select-all"> {{ convertSha1()}} </span>
    </div>
    <div class="algo">
      <span class="title">SHA256</span>
      <span class="select-all"> {{ convertSha256()}} </span>
    </div>
    <div class="algo">
      <span class="title">MD5</span>
      <span class="select-all"> {{ convertMd5()}} </span>
    </div>
    <div class="algo">
      <span class="title">Base64</span>
      <span class="select-all"> {{ convertBase64()}} </span>
    </div>
  </div>
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
.select-all{
  user-select: all;
  overflow-wrap: break-word;
}

.input-block{
  font-size: 2rem;
  margin-bottom: 1rem;
}

.input-text{
  padding: 5px;
  font-size:2rem;
  width: 90%;
  display: inline-block;
}
</style>
