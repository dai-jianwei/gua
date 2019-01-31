<template>
  <div :style="color" class="select" @click="areaClick">
    <span>{{ language }}</span>
    <img :class="{'turn':show}" src="../../assets/images/asset_gathering_icon_open@2x.png" alt="">
    <ul v-show="show" :style="backgroundColor" :class="{'top': position == 'top', 'bottom': position == 'bottom'}" >
      <li :class="{'actived': language == '中文'}" @click="itemClick('zh')">中文</li>
      <li :class="{'actived': language == '繁體中文'}" @click="itemClick('tw')">繁體中文</li>
      <li :class="{'actived': language == 'English'}" @click="itemClick('en')">English</li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    position: {
      type: String,
      default: 'top'
    },
    backgroundColor: {
      type: String,
      default: 'background-color:#fff;'
    },
    color: {
      type: String,
      default: 'color:#4d4d4d;'
    }
  },
  data () {
    return {
      show: false
    }
  },
  computed: {
    language () {
      if (this.$i18n.locale === 'en') {
        return 'English'
      } else if (this.$i18n.locale === 'tw') {
        return '繁體中文'
      } else {
        return '中文'
      }
    }
  },
  methods: {
    // 地区选择框点击
    areaClick () {
      this.show = !this.show
    },
    itemClick (lang) {
      this.$i18n.locale = lang
    }
  }
}
</script>

<style lang="less" scoped>
 .select{
    position: relative;
    width: 100%;
    height: 100%;
    color:#4D4D4D;
    font-size: 13px;
    text-align: right;
    span{
      line-height: 50px;
      cursor: pointer;
    }
    img{
      width: 8px;
    }
    img.turn{
      transform: rotate(180deg);
    }
    ul.top{
      bottom:calc(100% + 10px) !important;
    }
    ul.top:before{
      right:30%;
      top: 100% !important;
      border-bottom: 0;
    }
    ul.bottom{
      top:calc(100% + 10px) !important;
    }
    ul.bottom:before{
      right:30%;
      bottom: 100% !important;
      border-top: 0;
    }
    ul.left{
      right:calc(100% + 10px) !important;
    }
    ul.left:before{
      top:30%;
      left: 100% !important;
      border-right: 0;
    }
    ul.right{
      left:calc(100% + 10px) !important;
    }
    ul.right:before{
      top:30%;
      right: 100% !important;
      border-left: 0;
    }
    ul:before{
      position: absolute;
      content: " ";
      border: 6px solid #ffffff;
      border-left-color: transparent;
      border-right-color: transparent;
    }
    ul{
      position: absolute;
      left: -15px;
      width: calc(100% + 15px);
      padding:5px 0;
      border-radius: 4px;
      background-color: #ffffff;
      box-shadow: 0 2px 12px 0 rgba(0,0,0,.1);
      li{
        height:35px;
        line-height: 35px;
        padding-left:15px;
        text-align: left;
        cursor: pointer;
      }
      li.actived{
        background-color: #f5f7fa;
        color: #739FFF;
      }
    }
  }
</style>
