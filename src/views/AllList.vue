<template>
  <div class="home">
    <!-- トップページ -->
    <div class="main-page">
      <h3></h3>
      <div class="list-table">
        <table class="table">
          <thead>
            <tr>
              <th>ユーザーID</th>
              <th>報告数</th>
              <th></th>
            </tr>
            <tr v-for="item in simplify_list" :key="item.id">
              <td>@{{item.userID}}</td>
              <td>{{item.amount}}件</td>
              <td>
                <button class="btn btn-sm btn-outline-dark">詳細</button>
              </td>
            </tr>
          </thead>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import {ref,onMounted} from 'vue'
import axios from 'axios'
export default {
  name: 'Home',
  setup(){
    let simplify_list = ref([])

    let sorted_list = ref([])

    let search_word = ref('')

    const getList=async()=>{
      let data = await axios.get('https://sheets.googleapis.com/v4/spreadsheets/15kYNpG-0Pq34JV4HC8LiWI8o_yh-KZv6niWaaamQ7_Q/values/重複削除!A2:D10000?key=AIzaSyBYGo-htizvE31sI-GGUkMRsK0nZ7i5Wmw')

      for(let i=0; i<data.data.values.length; i++){
        simplify_list.value.push(
          {
            userID: data.data.values[i][0],
            amount: data.data.values[i][2],
          }
        )

        sorted_list.value = simplify_list.value
      }
    }

    const sortList=()=>{
      sorted_list.value = simplify_list.value.filter(item_data => {
        return item_data['userID'].toUpperCase().includes(search_word.value.toUpperCase())
      })
    }

    onMounted(()=>{
      getList()
    })
    return{
      simplify_list,
      sorted_list,
      search_word,
      getList,
      sortList
    }
  }
}
</script>