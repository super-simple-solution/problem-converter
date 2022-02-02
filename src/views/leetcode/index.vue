<script setup>
import { ref, watch } from 'vue'
import { parseContent } from './index.js'
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import json from './data/data.json'
import json1 from './data/data1.json'
import json2 from './data/data2.json'
import json3 from './data/data3.json'
import json4 from './data/data4.json'

const jsonList = [json, json1, json2, json3, json4]
const index = ref(4)
let content = jsonList[index.value].content
let contentRes = ref(parseContent(content))

watch(index, (val) => {
  console.log(val, 'val')
  content = jsonList[val]?.content
  if (!content) return
  contentRes.value = parseContent(content)
})
</script>

<template>
  <div style="width: 800px">
    <input v-model.number="index" />
    <div v-html="contentRes"></div>
  </div>
</template>
