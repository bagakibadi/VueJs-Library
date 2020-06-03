<template>
<div>
  <div class="head">
   <img class="images" :src="cover">
  </div>
        <router-link to="/home" class="back"><img src="../../assets/img/Arrow.png" alt="">
        </router-link>
        <div class="btntambah" v-if="dataUser.result[0].role_id == 1">
            <a href="#exampleModal" data-toggle="modal" data-target="#exampleModal"
             class="edit">Edit</a>
            <a href="#delete" class="delete">Delete</a>
        </div>
        <div class="container-close" id="delete">
            <div class="close-form">
                <a href="">X</a>
                <h2>Yakin Ingin Menghapus Data ?</h2>
                <div class="tombol">
                    <button class="btn btn-danger" @click="deleteBook">Yes</button>
                  <a href="#"> <button class="btn btn-secondary">No</button></a>
                </div>
            </div>
        </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HeaderDetail',
  data() {
    return {
      dataUser: {},
    };
  },
  props: ['cover'],
  mounted() {
    const container = document.querySelector('.container');
    container.style.backgroundImage = `url("${this.cover}")`;
  },
  methods: {
    deleteBook() {
      axios.delete(`${process.env.VUE_APP_API_MENU}book/${this.$route.params.id}`)
        .then((res) => {
          // eslint-disable-next-line no-unused-expressions
          res.data;
          this.$router.push('/home');
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  created() {
    axios.get(`${process.env.VUE_APP_API_MENU}user/${localStorage.idUser}`)
      .then((res) => {
        this.dataUser = res.data;
        // console.log(this.dataUser);
      })
      .catch((err) => {
        console.log(err);
      });
  },
  computed: {
    style() {
      return `background-image: ${this.cover.image}`;
    },
  },
};
</script>

<style scoped>
.head{
  position: relative;
  width: 100%;
  height: 454px;
}
.images {
    /* background-position: center center; */
    /* background-size: cover; */
    width: 100%;
    height: 454px;
    /* position: relative; */
    object-fit: cover;
}
.back {
    position: absolute;
    width: 30px;
    height: 30px;
    display: block;
    background: white;
    border-radius: 300px;
    padding-left: 13px;
    padding-top: 8px;
    padding-bottom: 35px;
    padding-right: 33px;
    top: 20px;
    left: 20px;
}
.edit {
    text-decoration: none;
    color: white;
    margin-right: 12px;
}
.delete {
    text-decoration: none;
    color: white;
}
.btntambah {
    position: relative;
    float: right;
    margin-top: 10px;
    margin-right: 40px;
    font-family: Airbnb Cereal App Bold;
    font-size: 30px;
}

.container-close {
            position: fixed;
            overflow: hidden;
            width: 0;
            height: 0;
            top: 0;
            left: 0;
            padding-top: 80px;
            transition: .5s ease-in;
            background-color: rgba(0, 0, 0 , 0);
            font-family: 'Airbnb Cereal App';
            }
            .close-form {
            width: 450px;
            height: 300px;
            margin:  auto;
            border-radius: 10px;
            box-sizing: border-box;
            background-color: #fff;
            margin: 30px auto;
            box-sizing: border-box;
            font-family: 'Airbnb Cereal App';
            }
            .container-close:target {
            width: auto;
            height: auto;
            bottom: 0;
            right: 0;
            bottom: 0;
            left: 0;
            background-color:rgba(196, 196, 196, 0.4);
            opacity: .9;
            }
            .close-form a {
            display: block;
            width: 30px;
            height: 30px;
            margin-left: 120px;
            margin-top: -48px;
            padding-top: 10px;
            }
            .close-form .checked {
            display: block;
            margin: auto;
            margin-top: 70px;
            margin-bottom: 10px;
            width: 70px;
            height: 70px;
            }
            .close-form h2 {
            margin-top: 90px;
            text-align: center;
            font-size: 20px;
            }
            .close-form h2 span {
            font-weight: 900;
            }
            .tombol{
                margin-top: 20px;
               margin-left: 120px;
            }
            .tombol button{
                width: 100px;
                margin-right: 30px;
            }
</style>
