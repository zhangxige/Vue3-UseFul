<template>
  <mytitle />
  <Row :gutter="{ xs: 8, sm: 16, md: 24, lg: 32 }">
      <Col class="gutter-row" :span="5">
      <Scrollbar style="max-height: 500px" @scroll="onScroll" @scrollend="onScrollEnd">
          <List :split="false">
              <ListItem v-for="(data, index) in listData" :key="index">
                  <template #title>
                      <a href="#">
                        <RouterLink :to="data.description">{{ data.title }}</RouterLink>
                      </a>
                  </template>
                  <template #avatar>
                      <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
                  </template>
                  <template #description>
                      {{ data.description }}
                  </template>
              </ListItem>
          </List>
      </Scrollbar>
    </Col>
    <Col class="gutter-row" :span="18">
      <RouterView />
    </Col>``
  </Row>
</template>

<script setup lang="ts" APP_NAME="App">
import { onMounted, ref, watchEffect } from "vue";
import { UserService, landRelevant } from './api/api.ts'
import Mylist from "./components/mylist.vue";
import myswiper from "./components/myswiper.vue";
import mytitle from "./components/mytitle.vue";

onMounted(()=>{
  // login1()
  login2()
})
let a_str = ref('')

const login1 = async () => {
  const loginParams = {
    username: 'test',
    password: 'test',
  }
  console.log('login1')
  const res = await UserService.login1(loginParams)
  console.log(res)
}

const login2 = () => {
  const loginParams = {
    'name': 'Fred',
    'lastName': 'Flintstone'
  }
  console.log('login2')
  landRelevant.gettest(loginParams).then((res: any)=>{
  console.log(res.data)
  a_str.value = res.data['a']
  })
}

const login3 = () => {
  const loginParams = {
    'name': 'Fred',
    'lastName': 'Flintstone'
  }
  console.log('login3')
  landRelevant.posttest(loginParams).then((res: any)=>{
  console.log(res.data)
  })
}

    const listData = ref([
    {
        title: 'What is Image?',
        description: 'Image',
        content: 'content'
    },
    {
        title: 'What is Color?',
        description: 'Color',
        content: 'content'
    },
    {
        title: 'What is Brightness?',
        description: 'Brightness',
        content: 'content'
    },
    {
        title: 'What is Contrast?',
        description: 'Contrast',
        content: 'content'
    },
    {
        title: 'What is Noise?',
        description: 'Noise',
        content: 'content'
    },
        {
        title: 'What is Clarity?',
        description: 'Clarity',
        content: 'content'
    },
        {
        title: 'What is Exposure?',
        description: 'Exposure',
        content: 'content'
    },
        {
        title: 'What is Saturation?',
        description: 'Saturation',
        content: 'content'
    },
        {
        title: 'What is Hue?',
        description: 'Hue',
        content: 'content'
    },
        {
        title: 'What is Sharpness?',
        description: 'Sharpness',
        content: 'content'
    },
        {
        title: 'What is White Balance?',
        description: 'WhiteBalance',
        content: 'content'
    },
    ])

    function onScroll(e: Event, direction: 'left' | 'right' | 'top' | 'bottom') {
    console.log('scroll', e, direction)
    }
    function onScrollEnd(e: Event, direction: 'left' | 'right' | 'top' | 'bottom') {
    console.log('scrollend', e, direction)
    }

</script>

<style lang="less" scoped>
.gutter-row {
  .grid-col {
    min-height: 30px;
    color: #000;
    text-align: left;
    border-radius: 0;
  }
  .gutter-box {
    background: #0092ff;
    padding: 8px 0;
  }
}
</style>