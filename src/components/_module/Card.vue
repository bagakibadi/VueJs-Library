<template>
<div>
  <div class="list">
    <h3>List Book</h3>
  </div>
  <div class="book">
    <div class="list-book" v-for="getAll in books" :key="getAll.result">
      <div class="gambar">
        <img :src="getAll.image" alt="...">
      </div>
      <h2><router-link :to="'/detail/'+getAll.id">{{getAll.title}}</router-link></h2>
      <p>{{getAll.description}}</p>
    </div>
  </div>
  <div class="lokqwe">
    <div class="pagination">
      <nav aria-label="Page navigation example">
        <ul class="pagination justify-content-center">
          <li class="page-item">
          <a class="page-link" style="cursor:pointer" @click="prevPages">Previous</a>
          </li>
          <li class="page-item" v-for="pagination in totalPage" :key="pagination">
            <a class="page-link" style="cursor:pointer"
          @click="pages(pagination)"  >{{pagination}}</a></li>
          <li class="page-item next">
          <a class="page-link" style="cursor:pointer" @click="nextPages">Next</a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</div>

</template>

<script>
import axios from 'axios';

export default {
  name: 'Card',
  data() {
    return {
      books: [],
      container: null,
      currentPage: 1,
      totalPage: [],
      url: `${process.env.VUE_APP_API_MENU}book?page=`,
    };
  },
  methods: {
    pages(id) {
      this.currentPage = 0 + id;
      axios.get(`${process.env.VUE_APP_API_MENU}book?page=${this.currentPage}`)
        .then((res) => {
          // eslint-disable-next-line prefer-destructuring
          this.books = res.data.result[2];
        });
    },
    nextPages() {
      if (this.currentPage === this.totalPage) {
        this.currentPage = this.totalPage;
      } else {
        this.currentPage += 1;
      }
      axios.get(`${process.env.VUE_APP_API_MENU}book?page=${this.currentPage}`)
        .then((res) => {
          // eslint-disable-next-line prefer-destructuring
          this.books = res.data.result[2];
          // eslint-disable-next-line prefer-destructuring
          this.totalPage = res.data.result[0];
        })
        .catch((err) => {
          console.log(err);
        });
    },
    prevPages() {
      if (this.currentPage === 1) {
        this.currentPage = 1;
      } else {
        this.currentPage -= 1;
      }
      axios.get(`${process.env.VUE_APP_API_MENU}book?page=${this.currentPage}`)
        .then((res) => {
          // eslint-disable-next-line prefer-destructuring
          this.books = res.data.result[2];
          // eslint-disable-next-line prefer-destructuring
          this.totalPage = res.data.result[0];
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  mounted() {
    axios.get(`${process.env.VUE_APP_API_MENU}book?page=${this.currentPage}`)
      .then((res) => {
        // eslint-disable-next-line prefer-destructuring
        this.books = res.data.result[2];
        // console.log(res);
        // eslint-disable-next-line prefer-destructuring
        this.totalPage = res.data.result[0];
      });
  },
};
</script>

<style scoped>
.lokqwe{
  position: relative;
  display: flex;
  justify-content: center;
  margin-bottom: 50px;
  margin-top: 30px;
}
.pagination{
  position: relative;
  /* margin-left: 100px; */
}
.list {
    height: 70px;
    background: white;
    font-size: 25px;
    padding-left: 50px;
    font-weight: bold;
}
.book {
    flex-wrap: wrap;
    height: auto;
    margin-left: 50px;
    margin-right: 50px;
    background: white;;
    position: relative;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    margin-bottom: 20px;
}
.list-book {
    position: relative;
    margin-top: 50px;
    width: 320px;
    height: 340px;
    border-radius: 15px;
    box-shadow: 0px 4px 25px rgba(0, 0, 0, 0.25);
    background: #fff;
    display: flex;
    flex-direction: column;
}
.gambar img {
    object-fit: cover;
    border-radius: 15px 15px 0px 0px;
    width: 100%;
    height: 200px;
}
.list-book h2 a {
    display: flex;
    justify-content: center;
    font-size: 22px;
    color: #424242;
    font-weight: bolder;
}
.list-book p {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 14px;
    line-height: 20px;
    margin-left: 18px;
    margin-top: 10px;
    color: #424242;
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 4;
    -webkit-box-orient: vertical;
}
/* @media only screen and (max-width: 800px) {
  .pagination {
    margin-top: -430px;
  }
} */
</style>
