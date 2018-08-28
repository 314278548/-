<template>
    <div class="main clearfix">
      <!-- 主体内容 -->
        <article>
            <div class="card" v-for="obj in arr" :key="obj.id" :ref="'btns'+obj.id">
                <div class="title">
                    <div class="from">{{obj.from}}</div>
                    <div class="auther">
                      <img src="../assets/logo.png" >
                      {{obj.auther}}
                      </div>
                  </div>              
                <div class="content">
                    <h2 class="h1">{{obj.h1}}</h2>
                    <div v-if="!obj.more" class="introduce">  
                      <p>{{obj.introduce | introduceFilter(obj.more)}}<a @click="readMore(obj)" v-show="!obj.more">阅读全文</a></p>
                    </div>
                    <div v-else class="detail">
                      <p>{{obj.introduce}}</p>
                    </div>
                </div>
                <div class="btns" :style="btns_style">
                <!-- <div class="btns" :ref="obj.more?'btns'+obj.id:null"> -->
                  <ul>
                    <li class="up" @click="up(obj)" :style="obj.style.up_style">{{obj.btnsState.up.flag}} {{obj.btnsState.up.num}}</li>
                    <li class="down" :style="obj.style.down_style" @click="down(obj)">▽</li>
                    <li class="comment">991评论</li>
                    <li class="share">分享</li>
                    <li class="collect">收藏</li>
                    <li class="thanks">感谢</li>
                    <li class="close" v-if='obj.more' @click="obj.more = false">收起</li>
                  </ul>
                </div>              
            </div>
          </article>  
        <!-- 侧边栏 -->
        <aside></aside>
        <transition   v-on:before-enter="beforeEnter"
  v-on:enter="enter"
  v-on:after-enter="afterEnter"
   v-on:before-leave="beforeLeave"
  v-on:leave="leave"
  v-on:after-leave="afterLeave"
  >
           <div class="public_btns" v-if="btns">
                  <ul>
                    <li class="up">赞同</li>
                    <li class="down">▽</li>
                    <li class="comment">991评论</li>
                    <li class="share">分享</li>
                    <li class="collect">收藏</li>
                    <li class="thanks">感谢</li>
                    <li class="close">收起</li>
                  </ul>
            </div>
        </transition> 
    </div>
</template>

<script>
export default {
  data() {
    return {
      refs: [],
      btns: false,
      arr: [
        {
          id: 1,
          from: "热门内容,CSS3入门",
          introduce:
            "做技术的话，前端能干十年，然后失业，而且每年技术翻一遍，正常五年不学习的话就差不多挂了后端技术不错的的话能干15年，没掌握核心技术的话，一样失业，做嵌入式或者C++的话，牛人可以干到50其实都一个鸟样，公务员，事业单位，体制内央企，才是牛逼啊你觉得你前几年牛逼，风光无限，年薪几十万，别人后三十年吊打你而且我告诉你，没有哪个公司核心业务在前端的",
          auther: "吴凯宇",
          h1: "你是从哪个细节发现女朋友、老婆出轨的？",
          btnsState: {
            up: { flag: "赞同", num: 30 },
            comment: 991,
            collect: false
          },
          style: {
            up_style: {},
            down_style: {}
          },
          more: false
        },
        {
          id: 2,
          from: "热门内容,CSS3入门",
          introduce:
            "我老家，18线城市，14年崩过一次。 12、13年房价高涨，民间借贷横行。房价从2000+飙涨到6000+。整个城市扩容一倍都不止。 全民投资。要不买房啊啊啊",
          auther: "吴凯宇",
          h1: "你是从哪个细节发现女朋友、老婆出轨的？",
          btnsState: {
            up: { flag: "赞同", num: 30 },
            comment: 991,
            collect: false
          },
          style: {
            up_style: {},
            down_style: {}
          },
          more: false
        },
        {
          id: 3,
          from: "热门内容,CSS3入门",
          introduce:
            "我老家，18线城市，14年崩过一次。 12、13年房价高涨，民间借贷横行。房价从2000+飙涨到6000+。整个城市扩容一倍都不止。 全民投资。要不买房啊啊啊",
          auther: "吴凯宇",
          h1: "你是从哪个细节发现女朋友、老婆出轨的？",
          btnsState: {
            up: { flag: "赞同", num: 30 },
            comment: 991,
            collect: false
          },
          style: {
            up_style: {},
            down_style: {}
          },
          more: false
        },
        {
          id: 4,
          from: "热门内容,CSS3入门",
          introduce:
            "我老家，18线城市，14年崩过一次。 12、13年房价高涨，民间借贷横行。房价从2000+飙涨到6000+。整个城市扩容一倍都不止。 全民投资。要不买房啊啊啊",
          auther: "吴凯宇",
          h1: "你是从哪个细节发现女朋友、老婆出轨的？",
          btnsState: {
            up: { flag: "赞同", num: 30 },
            comment: 991,
            collect: false
          },
          style: {
            up_style: {},
            down_style: {}
          },
          more: false
        },
        {
          id: 5,
          from: "热门内容, 来自: 程序员",
          introduce:
            "我只是一个代码的搬运工，也就是一名标准码农。       一提到码农，其他行业，特别是妹子！就会想到屌丝，秃顶，油腻，加班，熬夜，通宵等等。其实不然，码农固然少不了加班，但其实，码农的工作环境和工作状态是非常好的，毕竟坐办公室，吹着空调，还能泡杯茶喝。BAT没有进去，暂且不聊，且谈我自己的公司，虽然不是什么大公司，但也算是能搬得出台面的那种。首先福利待遇非常好，每到节假日都会有各种福利活动，比如徒步，马拉松，旅游啊。然后就是工作状态，平时其实最怕闲，码农在没有项目的时候，闲一个星期，一个月，都是很正常的（外包公司的小伙伴不要抬杠哟），而闲的时候，上班就是刷刷头条，刷刷知乎，然后就是各个群里吹水。当然，这些都是像我这样的菜鸡码农的日常生活，现在的我，也想进一下BAT，所以，开始在闲的时候学习，提高自己。       码农忙的时候，加班是很正常的，项目紧的话，可能每天都要10点以后，甚至通宵，都是家常便饭，但是，也不会一直这样忙，都是有忙有闲。       回到正题，正常情况下，作为一名屌丝码农，我的日常生活就是，7:50起床，洗漱过后，九点左右到公司（我们公司不用打卡，所以不存在迟到），然后开电脑，开编辑器，开始刷头条，刷知乎，然后聊聊天，一上午就过去了，12:00吃个饭（公司有食堂管饭），和同事打两把王者，然后睡午觉，13:30左右醒，出去溜达溜达，回来吃个水果（公司提供水果），然后15:00左右开始工作，写一点东西，工作量自己看呗，多的话，可能就写到18:00下班，不多的话，可能就写一两个小时，然后就接着干其他事去了。下班后，偶尔天气不错，会在旁边的球场打会儿篮球。大多数都是按部就班的坐地铁回去吃个饭，有时候自己做饭，有时候在外面吃。吃完饭后刷会儿抖音，半个小时左右，然后打开Keep，跟着做半小时运动，再去洗个澡，开始学习新的技术，之前还学了很久的吉他，但是可能不够热爱，渐渐的就放弃了。学习到22:00左右，开始玩游戏，吃鸡或者打王者，玩到12点左右，有人就聊会儿天，没人就酝酿一下准备睡觉了。     日子就是这样一天一天的重复，感情生活自然是没有的，习惯一个人单身了，虽然有时候也羡慕别人都是成双成对，但是也不是必需，重要的还是提高自己嘛。所以平时尽量精致的生活，会买面膜，护肤品之类的，也会提高生活质量，偶尔吃一顿大餐，给自己买双耐克的新球鞋，或者买件CK的短袖，会注意自己的形象，学会打扮自己，哈哈，虽然没有人看，但是也乐在其中。     当然现在的我不想当一名码农啦，我也想当BAT的程序猿，所以，开始努力学习啦，上班学习，下班学习，不再浪费时间了，希望通过努力，有一天能像各位程序猿大佬一样优秀。",
          auther: "吴凯宇",
          h1: "正在工作的程序员，生活状态什么样？",
          btnsState: {
            up: { flag: "赞同", num: 30 },
            comment: 991,
            collect: false
          },
          style: {
            up_style: {},
            down_style: {}
          },
          more: false
        },
        {
          id: 6,
          from: "热门内容, 来自: 程序员",
          introduce:
            "我只是一个代码的搬运工，也就是一名标准码农。       一提到码农，其他行业，特别是妹子！就会想到屌丝，秃顶，油腻，加班，熬夜，通宵等等。其实不然，码农固然少不了加班，但其实，码农的工作环境和工作状态是非常好的，毕竟坐办公室，吹着空调，还能泡杯茶喝。BAT没有进去，暂且不聊，且谈我自己的公司，虽然不是什么大公司，但也算是能搬得出台面的那种。首先福利待遇非常好，每到节假日都会有各种福利活动，比如徒步，马拉松，旅游啊。然后就是工作状态，平时其实最怕闲，码农在没有项目的时候，闲一个星期，一个月，都是很正常的（外包公司的小伙伴不要抬杠哟），而闲的时候，上班就是刷刷头条，刷刷知乎，然后就是各个群里吹水。当然，这些都是像我这样的菜鸡码农的日常生活，现在的我，也想进一下BAT，所以，开始在闲的时候学习，提高自己。       码农忙的时候，加班是很正常的，项目紧的话，可能每天都要10点以后，甚至通宵，都是家常便饭，但是，也不会一直这样忙，都是有忙有闲。       回到正题，正常情况下，作为一名屌丝码农，我的日常生活就是，7:50起床，洗漱过后，九点左右到公司（我们公司不用打卡，所以不存在迟到），然后开电脑，开编辑器，开始刷头条，刷知乎，然后聊聊天，一上午就过去了，12:00吃个饭（公司有食堂管饭），和同事打两把王者，然后睡午觉，13:30左右醒，出去溜达溜达，回来吃个水果（公司提供水果），然后15:00左右开始工作，写一点东西，工作量自己看呗，多的话，可能就写到18:00下班，不多的话，可能就写一两个小时，然后就接着干其他事去了。下班后，偶尔天气不错，会在旁边的球场打会儿篮球。大多数都是按部就班的坐地铁回去吃个饭，有时候自己做饭，有时候在外面吃。吃完饭后刷会儿抖音，半个小时左右，然后打开Keep，跟着做半小时运动，再去洗个澡，开始学习新的技术，之前还学了很久的吉他，但是可能不够热爱，渐渐的就放弃了。学习到22:00左右，开始玩游戏，吃鸡或者打王者，玩到12点左右，有人就聊会儿天，没人就酝酿一下准备睡觉了。     日子就是这样一天一天的重复，感情生活自然是没有的，习惯一个人单身了，虽然有时候也羡慕别人都是成双成对，但是也不是必需，重要的还是提高自己嘛。所以平时尽量精致的生活，会买面膜，护肤品之类的，也会提高生活质量，偶尔吃一顿大餐，给自己买双耐克的新球鞋，或者买件CK的短袖，会注意自己的形象，学会打扮自己，哈哈，虽然没有人看，但是也乐在其中。     当然现在的我不想当一名码农啦，我也想当BAT的程序猿，所以，开始努力学习啦，上班学习，下班学习，不再浪费时间了，希望通过努力，有一天能像各位程序猿大佬一样优秀。",
          auther: "吴凯宇",
          h1: "正在工作的程序员，生活状态什么样？",
          btnsState: {
            up: { flag: "赞同", num: 30 },
            comment: 991,
            collect: false
          },
          style: {
            up_style: {},
            down_style: {},
            owner_style: {}
          },
          more: false
        }
      ],
      btns_style: {}
    };
  },
  methods: {
    up(data) {
      if (data.btnsState.up.flag == "赞同") {
        data.style.up_style = {
          color: "white",
          "background-color": "#42b983"
        };
        data.btnsState.up.num += 1;
        data.btnsState.up.flag = "已赞同";
      } else {
        data.style.up_style = {};
        data.btnsState.up.flag = "赞同";
        data.btnsState.up.num -= 1;
      }
    },
    down(data) {
      if (data.btnsState.up.flag == "已赞同") {
        data.style.up_style = {};
        data.btnsState.up.flag = "赞同";
        data.btnsState.up.num -= 1;

        data.style.down_style = {
          color: "white",
          "background-color": "#42b983"
        };
      } else {
        data.style.down_style = {};
      }
    },
    readMore(data) {
      data.more = true;
      // btns = this.$refs[ref][0]
      // console.log(data.id)

      let el = this.arr.filter(function(el) {
        if (el.id == data.id) {
          return el;
        }
      });
      let ref = this.$refs["btns" + el[0].id][0];
      this.refs.push(ref);

      window.onscroll = function() {
        for (const key in this.refs) {
          ref = this.refs[key];
          if (
            ref.clientHeight > 750 &&
            ref.clientHeight + ref.offsetTop - 54 > //元素距离文档顶 + 元素高度 == 屏幕显示高度  + 文档滑动条滑动高度  元素底部与浏览器底部触碰
              document.documentElement.scrollTop +
                document.documentElement.clientHeight &&
            ref.offsetTop + ref.clientHeight * 0.45 <
              document.documentElement.scrollTop +
                document.documentElement.clientHeight
          ) {
            this.btns = true;
            return;
          } else {
            this.btns = false;
          }
        }
      }.bind(this);
    },
    beforeEnter: function(el) {
      el.style.transform = "translateY(20px)"; //初始位置
    },
    // 此回调函数是可选项的设置
    // 与 CSS 结合时使用
    enter: function(el, done) {
      el.offsetTop;
      el.style.transition = "transform .5s ease";
      el.style.transform = "translateY(0px)";
      done();
    },
    afterEnter: function(el) {},
    beforeLeave: function(el) {},
    // 设置过渡离开完成时地组件状态
    leave: function(el, done) {
      done();
    },
    // 设置过渡离开完成之后的组件状态
    afterLeave: function(el) {
      // ...
    }
  },
  filters: {
    introduceFilter(str, more) {
      return more ? str : str.substr(0, 76) + "...";
    }
  },
  mounted() {}
};
</script>


<style lang="less" scoped>
.main {
  width: 1000px;
  margin: 0 auto;
  // height: 900px;
  // border: 1px solid;
  padding-top: 100px;

  article {
    width: 80%;
    height: 100%;
    float: left;

    .card {
      width: 654px;
      // height: 183px;
      padding: 16px 20px;
      background-color: white;
      border-radius: 5px;
      box-shadow: 0 1px 3px rgba(26, 26, 26, 0.1);
      font-size: 15px;
      margin-bottom: 20px;

      .title {
        width: 654px;
        height: 52px;
        margin-bottom: 14px;

        .from {
          color: #8590a6;
          height: 20px;
          margin-bottom: 8px;
        }

        .auther {
          height: 24px;
          font-weight: 600;
          color: black;
          line-height: 24px;
          img {
            width: 24px;
            height: 24px;
            vertical-align: middle;
          }
        }
      }

      .content {
        width: 654px;
        // height: 131px;

        .h1 {
          height: 28px;
          font-size: 18px;
        }

        .introduce,
        .detail {
          margin-top: 9px;
          line-height: 1.67;
        }
        a {
          text-decoration-line: none;
          color: #175199;
        }
      }

      .btns {
        height: 32px;
        padding: 10px 0;

        ul li {
          float: left;
          height: 32px;
          line-height: 32px;
          color: #42b983;
          padding: 0 10px;
          border-radius: 3px;
          background-color: #42b98347;
          margin-right: 5px;
        }

        ul li:hover {
          cursor: pointer;
        }

        .close,
        .comment,
        .share,
        .collect,
        .thanks {
          padding-left: 20px;
          color: #8590a6;
          margin-left: 20px;
        }

        .comment {
          background: url(../assets/评论.png) no-repeat 0 8px;
        }

        .share {
          background: url(../assets/分享.png) no-repeat 0 8px;
        }

        .collect {
          background: url(../assets/星星.png) no-repeat 0 8px;
        }

        .thanks {
          background: url(../assets/爱心.png) no-repeat 0 8.5px;
        }

        .close {
          background: none;
          float: right;
        }
      }
    }
  }

  aside {
    float: left;
    height: 100%;
    width: 20%;
  }

  .public_btns {
    height: 32px;
    padding: 10px 0;
    width: 654px;
    position: fixed;
    bottom: 0;
    background-color: white;
    left: 50%;
    margin-left: -480px;

    ul li {
      float: left;
      height: 32px;
      line-height: 32px;
      color: #42b983;
      padding: 0 10px;
      border-radius: 3px;
      background-color: #42b98347;
      margin-right: 5px;
    }

    ul li:hover {
      cursor: pointer;
    }

    .close,
    .comment,
    .share,
    .collect,
    .thanks {
      padding-left: 20px;
      color: #8590a6;
      margin-left: 20px;
    }

    .comment {
      background: url(../assets/评论.png) no-repeat 0 8px;
    }

    .share {
      background: url(../assets/分享.png) no-repeat 0 8px;
    }

    .collect {
      background: url(../assets/星星.png) no-repeat 0 8px;
    }

    .thanks {
      background: url(../assets/爱心.png) no-repeat 0 8.5px;
    }

    .close {
      background: none;
      float: right;
    }
  }
}
</style>
