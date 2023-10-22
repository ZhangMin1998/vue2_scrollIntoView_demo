<template>
  <div class="app">
    <!-- Header 区域，固定不动 -->
    <header class="header">
      <!-- 这是 header 内容 -->
      <h1>Header</h1>
    </header>

    <!-- 主要内容区域，左侧选项和右侧内容 -->
    <div class="main">
      <!-- 左侧选项 -->
      <div class="left">
        <ul>
          <li
            v-for="item in items"
            :key="item.id"
            @click="scrollTo(item.id)"
            :class="{ active: item.id === activeItemId }"
          >
            {{ item.name }}
          </li>
        </ul>
      </div>

      <!-- 右侧内容 -->
      <div class="right" ref="right">
        <div
          v-for="item in items"
          :key="item.id"
          :id="'content-' + item.id"
          class="content"
        >
          {{ item.content }}
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.app {
  display: flex;
  flex-direction: column;
  /* height: 100vh; */
}

.header {
  background-color: #333;
  color: #fff;
  /* padding: 20px; */
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
}

.main {
  display: flex;
  flex: 1;
  /* margin-top: 74px; */
  /* margin-top: 60px; 保留 header 的高度 */
}

.left {
  /* height: 300px; */
  width: 200px;
  background-color: #eee;
  padding: 20px;
  /* overflow-y: auto; */
}

.left .active {
  background-color: #007bff;
  color: #fff;
}

.right {
  height: calc(100vh - 118px);
  flex: 1;
  padding: 20px;
  overflow-y: auto;
}

.content {
  margin-top: 20px;
  background-color: #f9f9f9;
  padding: 100px;
  border: 1px solid #ddd;
}
</style>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: '选项1', content: '内容1' },
        { id: 2, name: '选项2', content: '内容2' },
        { id: 3, name: '选项3', content: '内容3' },
        { id: 4, name: '选项4', content: '内容4' },
        { id: 5, name: '选项5', content: '内容5' },
        { id: 6, name: '选项6', content: '内容6' },
        { id: 7, name: '选项7', content: '内容7' },
        { id: 8, name: '选项8', content: '内容8' },
        { id: 9, name: '选项9', content: '内容9' },
        // 添加更多选项和内容
      ],
      activeItemId: null, // 当前选中的项的ID
    };
  },
  methods: {
    scrollTo(itemId) {
      console.log(itemId)
      this.activeItemId = itemId;
      const contentElement = this.$refs.right.querySelector(`#content-${itemId}`);
      console.log(contentElement);
      if (contentElement) {
        contentElement.scrollIntoView({ behavior: 'smooth', block: 'center' });
      }
    },
  },
};
</script>


<!-- <script>
export default {
  data() {
    return {
      selectedItemId: null,
      leftItems: [
        { id: 1, name: '选项1' },
        { id: 2, name: '选项2' },
        { id: 3, name: '选项3' },
        { id: 4, name: '选项4' },
        { id: 5, name: '选项5' },
        { id: 6, name: '选项6' },
        { id: 7, name: '选项7' },
        { id: 8, name: '选项8' },
      ],
      rightItems: [
        { id: 1, content: '内容1' },
        { id: 2, content: '内容2' },
        { id: 3, content: '内容3' },
        { id: 4, content: '内容4' },
        { id: 5, content: '内容5' },
        { id: 6, content: '内容6' },
        { id: 7, content: '内容7' },
        { id: 8, content: '内容8' },
      ],
    };
  },
  methods: {
    scrollToContent(itemId) {
      this.selectedItemId = itemId;
      const contentElement = this.$el.querySelector(`#${itemId}`);
      if (contentElement) {
        contentElement.scrollIntoView({ behavior: 'smooth' });
      }
    },
  },
};
</script> -->

