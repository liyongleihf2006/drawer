# drawer
vue抽屉组件

使用方式
```html
<template>
  <div>
    <button @click="openDrawer">打开</button>
    <drawer :open="open">
      <button @click="closeDrawer">关闭</button>
    </drawer>
  </div>
</template>
```
```js
import Drawer from './Drawer.vue';
export default {
  components:{
    Drawer
  },
  data:function(){
    return {
      open:false
    }
  },
  methods:{
      openDrawer(){
          this.open=true;
      },
      closeDrawer(){
          this.open=false;
      }
  }
}
```
