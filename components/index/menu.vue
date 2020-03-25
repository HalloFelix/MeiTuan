<template>
  <div class="m-menu">
    <dl class="nav"
        @mouseleave="mouseleave">
      <dt>全部分类</dt>
      <dd v-for="(item, idx) in menu"
          @mouseenter="mouseenter"
          :key="idx">
        <i :class="item.type" />{{item.name}}<span class="arrow" />
      </dd>
    </dl>
    <div class="detail"
         v-if="kind"
         @mouseenter="sover"
         @mouseleave="sout">
      <template v-for="(item, idx) in curdetail.child">
        <h4 :key="idx">{{item.title}}</h4>
        <span v-for="v in item.child"
              :key="v">{{v}}</span>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      kind: '',
      menu: [
        {
          type: 'food',
          name: '美食',
          child: [
            {
              title: '美食',
              child: ['代金券', '甜点', '饮品', '自助餐']
            }
          ]
        },
        {
          type: 'takeout',
          name: '外卖',
          child: [
            {
              title: '外卖',
              child: ['代金券1', '甜点2', '饮品3', '自助餐4']
            }
          ]
        },
        {
          type: 'food',
          name: '酒店',
          child: [
            {
              title: '酒店',
              child: ['酒店1', '酒店2', '酒店3', '酒店4']
            }
          ]
        },
        {
          type: 'takeout',
          name: '电影',
          child: [
            {
              title: '电影',
              child: ['最新上映1', '最新上映2', '最新上映3', '最新上映4']
            }
          ]
        }
      ]
    }
  },
  computed: {
    curdetail: function () {
      return this.menu.filter(item => item.type === this.kind)[0]
    }
  },
  methods: {
    mouseleave () {
      this._timer = setTimeout(() => {
        this.kind = ''
      }, 100)
    },
    mouseenter (e) {
      this.kind = e.target.querySelector('i').className
    },
    sover () {
      clearTimeout(this._timer)
    },
    sout () {
      this.kind = ''
    }
  }
}
</script>

<style>
</style>