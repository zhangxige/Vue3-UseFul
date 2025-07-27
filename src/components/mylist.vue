<template>
    <Scrollbar style="max-height: 500px" @scroll="onScroll" @scrollend="onScrollEnd">
        <List :split="false">
            <ListItem v-for="(data, index) in listData" :key="index">
                <template #title>
                    <a href="#">
                      <RouterLink to="/detail">{{ data.title }}</RouterLink>
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
    <RouterView />
</template>

<script setup lang="ts">
    import {ref, } from "vue";
    const listData = ref([
    {
        title: 'Vue Amazing UI Title 1',
        description: '1Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
    {
        title: 'Vue Amazing UI Title 2',
        description: '2Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
    {
        title: 'Vue Amazing UI Title 3',
        description: '3Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
    {
        title: 'Vue Amazing UI Title 4',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
    {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
        {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
        {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
        {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
        {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
        {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
        content: 'content'
    },
        {
        title: 'Vue Amazing UI Title 3',
        description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
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

<style lang="scss" scoped>
</style>