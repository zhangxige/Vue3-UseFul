<template>
  <Row :gutter="{ xs: 8, sm: 16, md: 24, lg: 32 }">
    <Col class="gutter-row" :span="8">
      <Button type="primary" ghost href="https://themusecatcher.github.io/vue-amazing-ui/" target="_blank">
        <template #icon>
          <img
            style="width: 1em; height: 1em"
            src="https://themusecatcher.github.io/vue-amazing-ui/amazing-logo.svg"
          />
        </template>
        Vue Amazing UI
      </Button>
    </Col>
    <Col class="gutter-row" :span="6">
        <InputSearch
            v-model:value="value"
            placeholder="input search text"
            search="Search"
            :search-props="{ type: 'primary', ghost: true }"
            @search="onSearch"
            >
            <template #icon>
                <CompassOutlined />
            </template>
        </InputSearch>
    </Col>
    <Col class="gutter-row" :span="8">
        <Avatar :size="40" src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
        <Avatar style="color: #f56a00; background-color: #fde3cf">U</Avatar>
        <Select
        :options="optionsCustom"
        label="name"
        value="id"
        v-model="selectedValue"
        />
    </Col>
  </Row>
</template>

<script lang="ts" setup>
import { ref, watchEffect } from 'vue'
import { SearchOutlined, CompassOutlined } from '@ant-design/icons-vue'
import type { SelectProps, SelectOption } from 'vue-amazing-ui'

const value = ref('')
watchEffect(() => {
  console.log('value', value.value)
})
function onSearch(value: string, e: MouseEvent | KeyboardEvent) {
  console.log('search', value, e)
}

const optionsCustom = ref<SelectOption[]>([
  {
    name: '北京市',
    id: 1
  },
  {
    name: '上海市',
    id: 2
  },
  {
    name: '纽约市',
    id: 3
  },
  {
    name: '旧金山',
    id: 4
  },
  {
    name: '布宜诺斯艾利斯',
    id: 5
  },
  {
    name: '伊斯坦布尔',
    id: 6
  },
  {
    name: '拜占庭',
    id: 7
  },
  {
    name: '君士坦丁堡',
    id: 8
  }
])
const selectedValue = ref<SelectProps['modelValue']>(5)
watchEffect(() => {
  console.log('selectedValue', selectedValue.value)
})

</script>

<style lang="less" scoped>
.gutter-row {
  .grid-col {
    min-height: 30px;
    color: #fff;
    text-align: center;
    border-radius: 0;
  }
  .gutter-box {
    background: #0092ff;
    padding: 8px 0;
  }
}
</style>