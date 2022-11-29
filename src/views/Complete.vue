<template>
  <div class="app">
    <h4>報告が完了しました。</h4>
    <button class="btn btn-outline-dark" @click="backHome()">戻る</button>
  </div>
</template>

<script>
import { useRouter } from 'vue-router'
export default {
  name:"Complete",
  setup(){
    const router = useRouter()
    const backHome=()=>{
      router.push('/')
    }
    return{
      backHome
    }
  }
}
</script>