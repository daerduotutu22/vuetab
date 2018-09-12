<template>
  <div>
    <!-- <h2>hello</h2> -->
    <my-tabs :tabList="tabList" :tabIndex="tabIndex" @changeTab="changeTab">
      <keep-alive>
        <component :is="currentContent">
        </component>
      </keep-alive>
    </my-tabs>
  </div>
</template>
<script>
import MyTabs from './tab.vue'
import One from './one.vue'
import Two from './two.vue'

export default {
  name: 'Home',
  components: {
    MyTabs,
    'one': One,
    'two': Two
  },
  data() {
    return {
      tabIndex: 0,
      currentContent: 'one',
      tabList: [
        {
          index: 0,
          name: '选项一',
          component: 'one'
        },
        {
          index: 1,
          name: '选项二',
          component: 'two'
        }
      ]
    }
  },
  methods: {
    // 切换选项卡
    changeTab: function(tab) {
      console.log(tab);
      this.tabIndex = tab.index
      this.currentContent = tab.component
    }
  }
}
</script>
