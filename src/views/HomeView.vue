<template>
  <div>
    <ListItem
      v-for="(item, index) in fakeListData"
      :key="item.id"
      :item-data="item"
      :badge-style="index === 0 ? 'yellow' : 'blue'"
      :tag-height="28"
      :show-imgs-sec="item.showImgsSec"
    />
  </div>
</template>
<script setup lang="ts">
import ListItem from '@/components/Home/ListItem.vue'

interface ListItemData {
  id: string
  author: string
  date: string
  title: string
  content: string
  tags: {
    type: string
    text: string
  }[]
  stats: {
    likes: number
    comments: number
    views: number
  }
  avatar: string
  coverImage?: string
  showImgsSec?: boolean
}

const fakeListData: ListItemData[] = [
  {
    id: '1',
    author: '張杰攻',
    date: '2021.09.12',
    title: '我好像为什么事情很悲哀，我想起"生命"',
    content:
      '有什么人能用绿竹作弓矢，射入云空，永不落下？我之想象，犹如长箭，向有什么人能用绿竹作弓矢，射入云空，永不落下？我之想象，犹如长箭，向有什么人能用绿竹作弓矢，射入云空，永不落下？我之想象，犹如长箭，向',
    tags: [
      { type: 'story', text: '故事' },
      { type: 'featured', text: '精选优质' },
    ],
    stats: {
      likes: 231,
      comments: 34,
      views: 786,
    },
    avatar: '/path/to/avatar1.jpg',
    showImgsSec: false,
  },
  {
    id: '2',
    author: '梁实秋',
    date: '2021.09.12',
    title: '谦让仿佛是一种美德，若想在眼前的实际生活！',
    content:
      '一群客人挤在客厅里，谁也不肯先坐，谁也不肯首座一群客人挤在客厅里，谁也不肯先坐，谁也不肯首座一群客人挤在客厅里，谁也不肯先坐，谁也不肯首座',
    tags: [{ type: 'article', text: '文章' }],
    stats: {
      likes: 231,
      comments: 34,
      views: 786,
    },
    avatar: '/path/to/avatar2.jpg',
    coverImage: '/path/to/cover.jpg',
    showImgsSec: true,
  },
]
</script>
