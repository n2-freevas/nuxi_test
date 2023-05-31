<script setup>
    console.log(useAppConfig())
    console.log(useRuntimeConfig())

    const nameValue = ref("")

    function acceptAndGo(){
      console.log('check')
    }
</script>

<template>
  <p>Vueをキャッチアップするついでに作った</p>
  <h1>僕との相性を<br>測定できるヤツ</h1>
  <div>
    <Input width="90%" v-model="nameValue" type="text" ph="おなまえ"/>
  </div>
  <div>
    <Button width="85%" :push-call-back="acceptAndGo">
      やってみる!
    </Button>
  </div>
</template>

<style lang="scss" scoped>
  Button{
    margin: 30px;
  }
  h1{
    font-size: 30px;
  }
  p{
    font-size: 12px;
    font-weight: bold;
  }
  div{
    div{
      padding: 10px 0;
      margin: 50px 0;
    }
  }
</style>
