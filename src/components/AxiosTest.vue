<template>
  <h2 class="boxTest">
        Axios Test
    </h2>  
    <button 
        type="button" 
        @click="onClickGetData">
        Axios Get
    </button>  
    <ul>    
        <li 
            v-for="(item, idx) in data_list.data" :key="idx">      
            <p>id : {{ item.id }}</p>      
            <p>email : {{ item.email }}</p>      
            <p>first_name : {{ item.first_name }}</p>      
            <p>last_name : {{ item.last_name }}</p>      
            <p>avatar : {{ item.avatar }}</p>    
        </li>  
    </ul>
</template>

<script>
import axios from "axios";

export default {
  name: "AxiosTest",
  data() {    
          return {      
              data_list: "null",    
          };  },  
          methods: {    
              onClickGetData() { axios.get(`https://reqres.in/api/users?/page=1`)        
              .then((res) => {  
                  // 성공인 경우        
                  console.log("Axios Get 성공");   
                  this.data_list = res.data;        
              })        
              .catch((res) => {    
                  // 실패인 경우      
                  console.log('실패')
                  console.error(res);        
              });    
          },  
      },
}
</script>

<style>
.boxTest {
  width: 200px;
  height: 50px;
  margin: 150px auto 50px;
}
</style>