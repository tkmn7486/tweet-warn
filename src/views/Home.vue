<template>
  <div class="home">
    <!-- トップページ -->
    <div class="main-page" v-if="now_view == 'main'">
      <h3></h3>
      <div class="list-table">
        <table class="table">
          <thead>
            <tr>
              <th>ユーザーID</th>
              <th>分類</th>
              <th></th>
            </tr>
            <tr v-for="item in simplify_list" :key="item.id">
              <td>@{{item.userID}}</td>
              <td>{{item.type}}</td>
              <td>
                <button class="btn btn-sm btn-outline-dark" @click="openDetail(item)">詳細</button>
              </td>
            </tr>
          </thead>
        </table>
      </div>
    </div>

    <!-- 詳細画面 -->
    <div class="detail-page" v-else-if="now_view == 'detail'">
      <div class="card mt-5">
        <table class="table">
          <tbody>
            <tr>
              <td>報告日時</td>
              <td>：</td>
              <td>{{selected_item.time}}</td>
            </tr>
            <tr>
              <td>ユーザーID</td>
              <td>：</td>
              <td>{{selected_item.userID}}</td>
            </tr>
            <tr>
              <td>分類</td>
              <td>：</td>
              <td>{{selected_item.type}}</td>
            </tr>
            <tr>
              <td>報告理由</td>
              <td>：</td>
              <td>{{selected_item.reason}}</td>
            </tr>
          </tbody>
        </table>
        <button class="btn btn-outline-dark" @click="now_view = 'main'">閉じる</button>
      </div>
    </div>

    <div class="error-page" v-else>
      error
    </div>
  </div>
</template>

<script>
import {ref,onMounted} from 'vue'
import axios from 'axios'
export default {
  name: 'Home',
  setup(){
    let now_view = ref('main')

    let simplify_list = ref([])

    let sorted_list = ref([])

    let search_word = ref('')

    let selected_item = ref([])

    const getList=async()=>{
      let data = await axios.get('https://sheets.googleapis.com/v4/spreadsheets/15kYNpG-0Pq34JV4HC8LiWI8o_yh-KZv6niWaaamQ7_Q/values/フォームの回答 1!A2:D10000?key=AIzaSyBYGo-htizvE31sI-GGUkMRsK0nZ7i5Wmw')

      for(let i=0; i<data.data.values.length; i++){
        simplify_list.value.push(
          {
            time: data.data.values[i][0],
            userID: data.data.values[i][1],
            type: data.data.values[i][2],
            reason: data.data.values[i][3],
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

    const openDetail=(item)=>{
      selected_item.value = []
      selected_item.value = {
        time: item.time,
        userID: item.userID,
        type: item.type,
        reason: item.reason
      }
      now_view.value="detail"
    }

    onMounted(()=>{
      getList()
    })
    return{
      now_view,
      simplify_list,
      sorted_list,
      search_word,
      selected_item,
      getList,
      sortList,
      openDetail
    }
  }
}
</script>
