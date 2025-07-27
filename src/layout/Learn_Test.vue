<template>
  <div class="learn-test">
    <h1>Learn and Test</h1>
    <p>This is the Learn and Test page.</p>
    <button @click="increment"> 响应式对象：{{ count }}</button>
    <button @click="clear_count"> 数据清零</button>
    <p>Has published books:</p>
    <span>计算属性： {{ publishedBooksMessage }}</span>
    <button @click="change_book_status"> 改变书籍状态</button>
    <div id="style-container">
        <button @click="change_style" :style="styleObject"> 改变样式</button>
    </div>
    <div id="author-if">
        <button @click="awesome = !awesome">(v-if)Toggle</button>
        <h1 v-if="awesome">Vue is awesome!</h1>
        <h1 v-else>Oh no 😢</h1>
    </div>
    <div id="my-object">
        <li v-for="(value, key, index) in myObject">
            {{ index }}. {{ key }}: {{ value }}
        </li>
        <button @click="change_myObject">change_myObject</button>
    </div>
    <div id="my-form">
        <p>Message is: {{ formmessage }}</p>
        <input v-model="formmessage" placeholder="edit me" />
    </div>
  </div>
</template>

<script lang="ts" setup>
    import { ref } from 'vue'
    import { reactive, computed } from 'vue'

    const count = ref(0)
    const increment = () => {
        count.value++
    }
    const clear_count = () => {
        count.value = 0
    }

    const author = reactive({
    name: 'John Doe',
    books: [
        'Vue 2 - Advanced Guide',
        'Vue 3 - Basic Guide',
        'Vue 4 - The Mystery'
    ]
    })

    // 一个计算属性 ref
    const publishedBooksMessage = computed(() => {
        return author.books.length == 3 ? 'Yes' : 'No'
    })
    const change_book_status = () => {
        if (author.books.length == 3) {
            author.books.push('Vue 4 - The Mystery')
        }
        else{
            // 添加一本新书
            author.books.pop()
        }
    }

    const styleObject = reactive({
        // 响应式对象
        color: 'red',
        fontSize: '30px'
    })
    let style_mark = ref(false)
    const change_style = () => {
        if (style_mark.value) {
            style_mark.value = false
            styleObject.color = 'blue'
        styleObject.fontSize = '20px'
        } else {
            style_mark.value = true
            styleObject.color = 'red'
            styleObject.fontSize = '30px'
        }
    }
    const awesome = ref(true)

    const myObject = reactive({
        title: 'How to do lists in Vue',
        author: 'Jane Doe',
        publishedAt: '2016-04-10'
    })
    const change_myObject = () => {
        if (myObject.title === 'How to do lists in Vue') {
            myObject.title = 'teaching in Vue 3'
            myObject.author = 'Jane Jone'
            myObject.publishedAt = '2025-05-10'
        } else {
            myObject.title = 'How to do lists in Vue'
            myObject.author = 'John Doe'
            myObject.publishedAt = '2020-01-01'
        }
    }
    const formmessage = ref('Hello Vue 3!')
</script>

<style scoped>
.learn-test {
  padding: 20px;
}
</style>
