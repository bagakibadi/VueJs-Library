<template>
<div>
  <div>
    <HeaderDetail v-bind:cover="books.result[0].image"/>
    <ContentDetail v-bind:book="books.result[0]"/>
  </div>
  <div>
    <div class="modal fade bd-example-modal-lg" id="exampleModal" tabindex="-1" role="dialog"
    aria-labelledby="myLargeModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-lg" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Add Book</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form enctype="multipart/form-data" @submit="updateBook">
              <div class="form-group">
                <label for="title-book" class="col-form-label">Title:</label>
                <input type="text" class="form-control" id="title-book"
                 v-model="books.result[0].title" >
              </div>
              <div class="form-group">
                <label for="message-text" class="col-form-label">Description:</label>
                <textarea class="form-control" id="message-text"
                 v-model="books.result[0].description" ></textarea>
              </div>
              <div class="form-group">
                <label for="author-book" class="col-form-label">Author:</label>
                <input type="text" class="form-control" id="author-book"
                 v-model="books.result[0].author" >
              </div>
              <div class="form-group">
                <label for="status" class="col-form-label">Status:</label>
                <input type="text" class="form-control" id="status"
                 v-model="books.result[0].status" >
              </div>
              <div class="form-group">
                <label for="category-book" class="col-form-label">Category:</label>
                <select v-model="books.result[0].id_category"  class="custom-select">
                  <option selected>Select Category</option>
                  <option value="1">Anak-Anak</option>
                  <option value="2">Agama</option>
                  <option value="3">Pengembangan Diri</option>
                  <option value="4">Komik</option>
                  <option value="5">Novel</option>
                </select>
                <div class="modal-footer">
                  <button type="button" class="btn btn-secondary"
                  data-dismiss="modal">Cancel</button>
                  <button type="submit" class="btn btn-primary">Save</button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios';
import HeaderDetail from '../../components/_module/HeaderDetail.vue';
import ContentDetail from '../../components/_module/ContentDetail.vue';

export default {
  name: 'Detail',
  components: {
    HeaderDetail,
    ContentDetail,
  },
  props: ['id'],
  data() {
    return {
      books: {},
    };
  },
  // updated() {
  //   if (!localStorage.password && !localStorage.idUser && this.$route.path !== '/login') {
  //     this.$router.push('/login');
  //   }
  // },
  mounted() {
    axios.get(`${process.env.VUE_APP_API_MENU}book/${this.id}`)
      .then((res) => {
        this.books = res.data;
      });
    console.log(process.env.DB_BOOK);
  },
  methods: {
    updateBook() {
      axios.patch(`${process.env.VUE_APP_API_MENU}book/${this.$route.params.id}`, {
        title: this.books.result[0].title,
        description: this.books.result[0].description,
        author: this.books.result[0].author,
        status: this.books.result[0].status,
        id_category: this.books.result[0].id_category,
      })
        .then((res) => {
          this.books = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style scoped>

</style>
