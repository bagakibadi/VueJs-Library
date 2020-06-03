<template>
    <div class="nvbr">
            <div class="select">
                <select class="">
                    <option value="">All Catagories</option>
                </select>
                <select class="">
                    <option value="">All Time</option>
                </select>
            </div>
            <div class="search">
                <input type="text" class="search-box" @input="searchBook" placeholder="Search book">
            </div>
            <div class="library">
                <a href="index.html"><img src="../../assets/img/buku.png" alt=""></a>
                <label for="">Library</label>
            </div>
        </div>
</template>

<script>
export default {
  name: 'Navbar',
};
</script>

<style scoped>
.nvbr {
    position: fixed;
    padding: 0px 50px;
    width: 100%;
    box-sizing: border-box;
    background: white;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);
    z-index: 9;
}
.select {
    position: relative;
    display: flex;
    width: 20%;
}
.login a {
    position: relative;
    z-index: 5;
    border: 2px solid black;
    padding: 5px 20px;
}
.select select {
    border: 1px solid #fff;
    background-color: transparent;
    width: 130px;
    height: 30px;
    z-index: 2;
    color: #424242;
    font-size: 17px;
}
.search {
    position: relative;
    display: flex;
    width: 45%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: transparent;
    z-index: 1;
}
.search input {
    font-size: 17px;
    color: #CACACA;
    font-family: Airbnb Cereal App;
    outline: none;
    width: 300px;
    height: 35px;
    padding: 5px 20px;
    border: 1px solid #CACACA;
    box-sizing: border-box;
    border-radius: 20px;
}
.library {
    position: relative;
    width: 10%;
    height: 60px;
    display: flex;
    align-items: center;
}
.library img {
    width: 50px;
    height: 50px;
}
@media only screen and (max-width: 800px) {
    .select {
        display: none;
    }
    .search {
        /* display: none; */
        left: 130px;
        width: 10%;
    }
    .search input{
        width: 200px;
    }
}
</style>
