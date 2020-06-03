<template>
  <div>
    <div class="button">
      <router-link to="/home">
      <i class='fas fa-arrow-left' style='font-size:36px'></i>
      </router-link>
    </div>
    <div class="header">
      <h1>History Peminjaman Buku</h1>
    </div>
    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">No</th>
          <th scope="col">Nama Peminjam</th>
          <th scope="col">Title</th>
          <th scope="col">Author</th>
          <th scope="col">status</th>
          <th scope="col" >Tanggal Peminjaman</th>
        </tr>
      </thead>
      <tbody v-for="loan in data.result" :key="loan">
        <tr>
          <th scope="row">1</th>
          <td>{{loan.fullname}}</td>
          <td>{{loan.title}}</td>
          <td>{{loan.author}}</td>
          <td>{{loan.status}}</td>
          <td>{{loan.borrowed_date}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'History',
  data() {
    return {
      data: [],
    };
  },
  methods: {
    getLoan() {
      axios.get(`${process.env.VUE_APP_API_MENU}borrowbook/1`)
        .then((res) => {
          this.data = res.data;
        });
    },
  },
  mounted() {
    this.getLoan();
  },
};
</script>

<style scoped>
.header{
  display: flex;
  justify-content: center;
  align-items: flex-end;
  height: 200px;
  padding-bottom: 50px;
}
.button{
  margin-left: 50px;
  margin-top: 50px;
}
</style>
