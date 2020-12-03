---
title: Vue3.0在JSX下如何使用插槽(slot)
date: 2020-12-3 23:51:00
categories: 
- Vue
---

在文档上没找到，使用搜索引擎也没见有人发表相关内容。最后在vuejs/jsx-next这个repo的README.md找到了解决方案，在这里分享给大家。

## 官方文档示例
注意: 在 jsx 中，应该使用 v-slots 代替 v-slot
```javascript
const App = {
  setup() {
    const slots = {
      foo: () => <span>B</span>
    };
    return () => (
      <A v-slots={slots}>
        <div>A</div>
      </A>
    );
  }
};

// or

const App = {
  setup() {
    const slots = {
      default: () => <div>A</div>,
      foo: () => <span>B</span>
    };
    return () => <A v-slots={slots} />;
  }
};
```


## 个人示例
xxx.vue
```html
<van-image
  round
  width="7rem"
  height="7rem"
  fit="cover"
  src="/img/AquaMinato.png"
  style="display: block; margin: 0 auto;"
>
  <template v-slot:loading>
    <van-loading type="spinner" size="20" />
  </template>
  <template v-slot:error>加载失败</template>
</van-image>
```

这里我虽然用的是TSX (TypeScript的JSX)，但用法应该和JSX是一样的。

xxx.tsx
```tsx
setup() {
  const slots = {
    loading: () => <van-loading type="spinner" size="20" />,
    error: () => <span>加载失败</span>
  }

  return () => (
    <div>
      <van-image
        round
        width="7rem"
        height="7rem"
        fit="cover"
        src="/img/AquaMinato.png"
        style="display: block; margin: 0 auto;"
        v-slots={slots}
      >
      </van-image>
    </div>
  )
}
```

## 参考资料
https://github.com/vuejs/jsx-next/blob/dev/packages/babel-plugin-jsx/README-zh_CN.md
