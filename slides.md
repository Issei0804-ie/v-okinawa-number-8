---
theme: seriph
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: defineModel使ってみた
mdc: true
addons:
  - '@katzumi/slidev-addon-qrcode'
  - slidev-addon-components
  - slidev-addon-rabbit
---

# Vue3.4で追加されたdefineModelを使ってみた

## issei

<!-- v0.0.0 -->

---

# 自己紹介

- 名前: issei
- 所属: 株式会社Relic
- 仕事: Laravel, Vue3
- 趣味: ビリヤード始めました🎱


<div class="absolute top-10 right-30">
  <img src="https://pbs.twimg.com/profile_images/1362727823966826496/3qxbX5mg_400x400.jpg" alt="Kani" class="w-50 h-50 object-contain" />
</div>

---

# Vue3.4について

- リリース日: 2023-12-29
  - なんとびっくりほぼ**1年前**
- Vue3.4で追加された`defineModel`について
  - なんとなく程度には機能を知っていた
  - まだドキュメントは読んでなかったので読むついでにまとめたのがこのスライド


---
layout: two-cols-header
---

# defineModel

- v-modelを使用するときに開発者体験を上げるマクロ

::left::

### defineModelを使用しない場合
```typescript
<script setup>
const props = defineProps(['modelValue'])
const emit = defineEmits(['update:modelValue'])
</script>

<template>
  <input
    :value="props.modelValue"
    @input="emit('update:modelValue', $event.target.value)"
  />
</template>
```
::right::
### defineModelを使用する場合
```typescript
<script setup>
const model = defineModel()

function update() {
  model.value++
}
</script>

<template>
  <div>Parent bound v-model is: {{ model }}</div>
  <button @click="update">Increment</button>
</template>
```

---

# defineModel

- `defineProps`のように型を書くこともできる

```typescript
const model = defineModel({ type: String })
```

- `required`も書ける

```typescript
const model = defineModel(
  { 
    type: String,
    required: true,
  }
)
```

- ということは、`default`も書いて良い

```typescript
const model = defineModel(
  { 
    type: String,
    required: true,
    default: 'hoge',
  }
)
```

---

# defineModelを使ってみた

- サクッとフォームを作ってみた
- フォーム動かす&&コード眺めて発表を終わりにする
- http://bit.ly/4gQBA7P


<QRCode
  value="http://bit.ly/4gQBA7P"
  :width="180"
  :height="180"
  color="4329B9"
/>
