# Quick installation
如何快速安装 VueUse

   在 Vue 项目中使用 VueUse，你可以通过 npm 或 yarn 安装它：
   
   npm install @vueuse/core
   或者yarn add @vueuse/core
   
   然后，在你的 Vue 组件中导入并使用所需的函数：
   
   ```
   import { useDark, useToggle } from '@vueuse/core';

   export default {

      setup() {

         const isDark = useDark();
         const toggleDark = useToggle(isDark);

         return { isDark, toggleDark };
       }
    };
  