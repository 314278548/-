<template> 
<div class="header">
   <!-- <el-col  :xl="2" :style="border"></el-col> -->
        <!-- <el-col  :xl="20" class="main" :style="border"> -->
          <div class="main">
          <ul>
               <li>
                 <form>
                   <input class="search" @focus="searchEvent" @blur="searchEvent" >
                   <img src="../assets/搜索.png">
                 </form>
            </li>
            <li>
            <div v-show="!focus" class="w_article">
              <a href="#">写文章</a>
            </div></li>
            </ul>
            </div>
        <!-- </el-col> -->
    <!-- <el-col :xl="2" :style="border"></el-col> -->
</div>
</template>

<script>
import { Row, Col } from "element-ui";
import search from "components/searchBox.vue";
export default {
  components: {
    "el-row": Row,
    "el-col": Col,
    search
  },
  data() {
    return {
      focus: false
    };
  },
  methods: {
    searchEvent(event) {
      event.type == "focus" ? (this.focus = true) : (this.focus = false);
    }
  }
};
</script>


<style lang="less" scoped>
.header {
  position: fixed;
  width: 100%;
  height: 70px;
  border-bottom: 1px solid rgb(228, 224, 224);
  background-color: white;
  box-shadow: 0 0 5px #888;
  .main {
    position: relative;
    background: white;
    height: 70px;
    margin: 0 auto;
    width: 80%;
    ul {
      left: 1190px;
      position: absolute;
      margin-top: 20px;
      li {
        display: inline-block;
        vertical-align: middle;

        form {
          position: relative;

          img {
            position: absolute;
            top: 7px;
            right: 7px;
          }

          img:hover {
            cursor: pointer;
          }
        }

        .search {
          width: 160px;
          padding: 0 30px 0 20px;
          height: 28px;
          border: 1px solid #e3e3e3;
          border-radius: 15px;
          outline: none;
          // background: url() 95% 7px no-repeat;
        }

        .search:focus {
          border-color: #42b983;
          box-shadow: 0 0 2px #42b983;
          width: 240px;
          transition: all 0.5s ease;
        }

        .w_article {
          height: 30px;
          text-align: center;
          line-height: 30px;
          background-color: #42b983;
          color: white;
          border-radius: 15px;
          padding: 0 15px;
          margin-left: 30px;
          a {
            color: white;
            text-decoration-line: none;
          }
        }
      }
    }
  }
}
</style>
