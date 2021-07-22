<template>
  <div class="aes">
    <img alt="Vue logo" src="../assets/Locked.svg"
      style="width:200px" v-if="aesType == 'encrypt'">
    <img alt="Vue logo" src="../assets/Key.svg" style="width:200px" v-if="aesType == 'decrypt'">
  </div>
  <div class="p-3 w-100 text-center mx-auto d-flex switchblock">
    <div class="btn btn-primary" v-on:click="aesType = 'encrypt';inputtext='';">Encrypt</div>
    <div class="btn btn-warning" v-on:click="aesType = 'decrypt';inputtext='';">Decrypt</div>
  </div>
  <div class="input-block">
    {{ inputType }}
    <input type="text" class="input-text" v-model.trim="inputtext"/>
    Secret key
    <input type="password" class="input-text" v-model.trim="secretkey"/>
  </div>
  <div class="block-style">
    <div class="algo" v-if="aesType == 'encrypt'">
      <span class="title">Cipher Text</span>
      <span class="select-all"> {{ encrypt()}} </span>
    </div>
    <div class="algo" v-if="aesType == 'decrypt'">
      <span class="title">Plain Text</span>
      <span class="select-all"> {{ decrypt()}} </span>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import AES from 'crypto-js/aes';
import UTF8 from 'crypto-js/enc-utf8';

export default {
  name: 'AES',
  data() {
    return {
      secretkey: '',
      inputtext: '',
      cipher: '',
      aesType: 'encrypt',
    };
  },
  components: {
  },
  computed: {
    inputType() {
      return this.aesType === 'encrypt' ? 'Plain Text' : 'Cipher Text';
    },
  },
  methods: {
    encrypt() {
      const ciphertext = AES.encrypt(this.inputtext, this.secretkey).toString();
      this.cipher = ciphertext;
      return (this.inputtext === '' || this.secretkey === '') ? '' : ciphertext;
    },
    decrypt() {
      try {
        const bytes = AES.decrypt(this.inputtext, this.secretkey);
        return bytes.toString(UTF8);
      } catch (error) {
        return '';
      }
    },
  },
};
</script>

<style scoped lang="scss">
@mixin tablet{
  @media(min-width: 1024px){
    @content;
  }
}
@mixin desktop{
  @media(min-width: 1400px){
    @content;
  }
}

.btn{
  font-size: 1.5rem;
}

.switchblock{
  width: 100%;
  justify-content: space-around;
  @include tablet(){
    width: 33% !important;
    justify-content: space-between;
  }
  @include desktop{
    width: 25% !important;
    justify-content: space-between;
  }
}
</style>
