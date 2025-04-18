<script setup>
import {computed, onBeforeUnmount, onMounted, ref} from "vue";

const q_list = ref([
  '如何办理入学？',
  '开学在哪里入学？',
  '报道时需要带什么证件？',
  '转专业有哪些条件？',
  '在哪儿查看学籍信息？',
  '怎么网上交学费？',
])

const left_col = ref(6)
const right_col = computed(() => 24 - left_col.value)

const viewportWidth = ref(window.innerWidth)
const updateViewport = () => {
  viewportWidth.value = window.innerWidth
}
onMounted(() => {
  window.addEventListener('resize', updateViewport)
})
onBeforeUnmount(() => {
  window.removeEventListener('resize', updateViewport)
})
updateViewport()

</script>

<template>
  <div class="banner">
    <img alt="" src="./assets/banner.png" style="width: 100%;"/>
  </div>
  <el-card class="card">
    <el-row>
      <el-col :span="left_col" :xs="0">
        <div style="margin: 20px;">
          <div class="title">
            常见问题列表
          </div>
          <a v-for="i in q_list" href="#">
            <ul class="line"><div class="text"><span style="color: red; margin-right: 10px;">◆</span>{{ i }}</div>
            </ul>
          </a>
        </div>
      </el-col>
      <el-col :span="right_col" :xs="24">
        <iframe
            allow="microphone"
            frameborder="0"
            src="http://wuhanzkun.oicp.net/chatbot/tNIK8Id8EX6L4Ig6"
            style="width: 100%; height: 50vh; min-height: 700px">
        </iframe>
      </el-col>
    </el-row>


  </el-card>
</template>

<style lang="scss" scoped>
.banner {
  height: 12vh;
}

.card {
  margin: 10px;
  border-radius: 20px;
}

.title {
  background-color: #d7050e;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 60px;
  color: white;
  font-size: 18px;
  letter-spacing: 3px;
}

.line {
  margin-top: 20px;
  padding-bottom: 10px;
  border-bottom: 1px dashed #ccc;
}

.text:hover {
  transform: translateX(10px);
}

</style>
