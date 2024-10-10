# Button component
VueUse 按钮组件学习笔记
1. 什么是 VueUse 按钮组件？

   在 VueUse 中，按钮组件可能不是一个特定的预制组件，但你可以利用 VueUse 提供的实用函数来创建自定义按钮组件。这些按钮组件可以包括加载状态、禁用状态、点击事件处理等。

2. VueUse 按钮组件的特点

   可定制性：可以自定义按钮的样式、大小、颜色和行为。
   
   响应式：可以响应用户的点击事件，并执行相应的操作。
   
   组合式 API：使用 Vue 3 的组合式 API 来构建按钮组件，提高代码的可维护性和可重用性。
3. 使用 VueUse 按钮组件的场景
   
   执行操作：如提交表单、触发 API 调用、打开模态框等。
    
    状态指示：显示加载状态、成功状态或错误状态。
4. 如何使用 VueUse 创建按钮组件
   
   在 Vue 项目中，你可以使用 VueUse 的 useClickOutside、useToggle 等函数来增强按钮组件的功能：
   ```
   <template>
  <button :disabled="isLoading" @click="handleClick">
    <template v-if="isLoading">加载中...</template>
    <template v-else>点击我</template>
  </button>
  </template>
```
<script setup>
import { ref } from 'vue';
import { useToggle } from '@vueuse/core';

const isLoading = ref(false);

const { toggle } = useToggle(isLoading);

const handleClick = async () => {
  toggle(); // 启用加载状态
  try {
    // 执行异步操作
    await new Promise((resolve) => setTimeout(resolve, 2000));
  } finally {
    toggle(); // 禁用加载状态
  }
};
</script>

<style scoped>
button {
  padding: 10px 20px;
  font-size: 16px;
  color: white;
  background-color: #007bff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:disabled {
  background-color: #cccccc;
}
</style>

```