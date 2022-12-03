<template>
  <div id="app">
    <el-input style="width: 200px" v-model="code"></el-input>
    <br />
    <cm-input style="width: 200px" v-model="code"></cm-input>
  </div>
</template>

<script>
import { CmInput } from './components/CodemirrorInput/';
export default {
  name: 'app',
  components: {
    CmInput
  },
  data() {
    return {
      code: "123123"
    }
  }
}
</script>

<style scoped>
</style>

