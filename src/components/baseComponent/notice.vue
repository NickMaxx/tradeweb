<!--  -->
<template>
  <div class="notice">
    <div class="wd fx-row fx-m-start">
      <div class="no-title">NEWS:</div>
      <div>
        <ul :class="marqueeClass"
          id="notice-list">
          <!-- 跑马灯效果，将li节点复制一份 -->
          <li v-for="(n, nidx) in news"
            :key="nidx"
            @click="gotoNoticeDetail(n.url)">
            {{n.text}}
          </li>
          <li v-for="(n, nidx) in news"
            :key="nidx+'i'"
            @click="gotoNoticeDetail(n.url)">
            {{n.text}}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 最多支持5条新闻，请后台一次最多控制5条返回
      news: [
        {
          text: '第十二届全国电子商务洽淡会在北京召开',
          url: 'https://www.baidu.com'
        },
        {
          text: '恭喜阿里巴巴在人工智能领域的又一重大突破',
          url: 'https://www.163.com'
        },
        { text: '马云说，未来十年最便宜的是房价', url: 'https://www.qq.com' },
        { text: '苹果黔驴技穷？股价下跌百分之十', url: 'https://www.sina.com' },
        {
          text: '小米发布最新旗舰，仅售人民币2499，将进军印度市场',
          url: 'https://www.taobao.com'
        }
      ]
    };
  },

  components: {},

  computed: {
    // 跑马灯的class名，最多支持新闻5条
    marqueeClass() {
      let arr = [
        'two-column-marquee',
        'three-column-marquee',
        'four-column-marquee',
        'five-column-marquee'
      ];
      let dataLength = this.news.length || 0;
      return arr[dataLength - 2];
    }
  },

  mounted() {},

  methods: {
    gotoNoticeDetail(url) {
      window.location.href = url;
    }
  }
};
</script>
<style lang='scss' scoped>
// 跑马灯的scss文件
@import '../../scss/marquee.scss';
.notice {
  clear: both;
  height: 44px;
  background: url(../../images/n_bg.jpg) repeat-x;
  .no-title {
    float: left;
    width: 70px;
    background: url(../../images/laba.jpg) no-repeat left center;
    color: #005194;
    font-size: 14px;
    height: 44px;
    padding-left: 30px;
    line-height: 44px;
    font-weight: bold;
  }
}
.notice .wd div {
  float: left;
  height: 44px;
}
.notice .wd div ul {
  clear: both;
}
.notice .wd div ul li {
  clear: both;
  height: 44px;
  line-height: 44px;
}
</style>