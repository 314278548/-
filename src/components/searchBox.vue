<template>
   <input class="search" type="text">
</template>

<script>
export default {};
</script >

<style scoped>
input.search {
  width: 216px;
  height: 30px;
  padding: 0 15px 0 30px;
  border: 1px solid rgb(228, 224, 224);
  color: #2c3e50;
  margin-right: 10px;
  transition: border-color 0.2s ease;
  box-sizing: border-box;
  border-radius: 15px;
  outline: none;
  background: url(../assets/搜索.png) 8px no-repeat;
  float: right;
}

input.search:focus{
  border: 1px solid #42b983
}


</style>
