<template>
  <div class="list-item">
    <div class="author-info">
      <img :src="itemData.avatar" :alt="itemData.author" class="avatar" />
      <span class="author">{{ itemData.author }}</span>
      <span class="date">{{ itemData.date }}</span>
    </div>

    <h2 class="title">{{ itemData.title }}</h2>
    <p class="content text-truncate-2-line">{{ itemData.content }}</p>
    <div class="imgs" v-if="showImgsSec">
      <div class="img-item flex-1"></div>
      <div class="img-item flex-1"></div>
      <div class="img-item flex-1"></div>
    </div>
    <div class="tags">
      <span
        v-for="tag in itemData.tags"
        :key="tag.type"
        class="tag"
        :style="{
          ...badgeStyles[badgeStyle],
          height: `${tagHeight}px`,
          lineHeight: `${tagHeight}px`,
        }"
      >
        {{ tag.text }}
      </span>
    </div>

    <div class="stats">
      <span>點贊 {{ itemData.stats.likes }}</span>
      <span>收藏 {{ itemData.stats.comments }}</span>
      <span>評論 {{ itemData.stats.comments }}</span>
      <span>觀看 {{ itemData.stats.views }}</span>
    </div>

    <img v-if="itemData.coverImage" :src="itemData.coverImage" class="cover-image" />
  </div>
</template>

<script lang="ts" setup>
interface ItemData {
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

interface Props {
  itemData: ItemData
  badgeStyle?: 'yellow' | 'blue' | 'green'
  tagHeight?: number
  showImgsSec?: boolean
}

withDefaults(defineProps<Props>(), {
  badgeStyle: 'yellow',
  tagHeight: 32,
  showImgsSec: false,
})

const badgeStyles = {
  yellow: {
    background: '#FFF7E6',
    color: '#D46B08',
  },
  blue: {
    background: '#E6F4FF',
    color: '#0958D9',
  },
  green: {
    background: '#F6FFED',
    color: '#389E0D',
  },
}
</script>

<style scoped lang="scss">
.list-item {
  padding: 16px;
  border-bottom: 1px solid #eee;

  .author-info {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 12px;

    .avatar {
      width: 32px;
      height: 32px;
      border-radius: 50%;
    }

    .date {
      color: #999;
    }
  }

  .title {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 8px;
  }

  .content {
    color: #666;
    margin-bottom: 12px;
  }

  .imgs {
    display: flex;
    gap: 8px;
    margin-bottom: 12px;

    .img-item {
      width: 100px;
      height: 100px;
      background-color: #f5f5f5;
      border-radius: 4px;
    }
  }

  .tags {
    display: flex;
    gap: 8px;
    margin-bottom: 12px;

    .tag {
      padding: 0 8px;
      border-radius: 4px;
      font-size: 12px;
      white-space: nowrap;
    }
  }

  .stats {
    display: flex;
    gap: 16px;
    color: #999;
    font-size: 14px;
  }

  .cover-image {
    margin-top: 12px;
    width: 100%;
    border-radius: 8px;
  }
}
</style>
