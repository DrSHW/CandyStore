<script setup lang="ts">
import { useData, withBase } from 'vitepress'
import type { Link } from '../types'
const data = useData()
const links = data.site.value.themeConfig.links as Link[]
const siteInfo = data.site.value
</script>

<template>
  <header>
    <a class="title" href="/">{{ siteInfo.title }}</a>
    <p class="sub-title">
      {{ siteInfo.description }}
    </p>
    <p>
      <a v-for="item in links" :key="item.name" :href="withBase(item.link)">
        <img
          :src="withBase(item.icon)"
          :alt="item.name"
          width="20"
          height="20"
        >
        <p>
          {{ item.name }}
        </p>
      </a>
    </p>
  </header>
</template>

<style lang="scss" scoped>
header {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 5rem auto 5rem;
  text-align: center;
}
header > *:not(:last-child) {
  margin-bottom: 2rem;
}
.title {
  letter-spacing: 0.2rem;
  font-size: 2.6rem;
  color: #444;
}
.title:active {
  color: #444;
}
.sub-title {
  letter-spacing: 0.1rem;
  font-size: 1.3rem;
}
p {
  display: flex;
  align-items: center;
}
p a {
  padding: 0 8px;
  height: 20px;
  object-fit: cover;
  transition: all 0.5s;
  &:hover {
    transform: scale(1.1, 1.1);
  }
  display: flex;
  flex-direction: column;
  align-items: center;
}
p a img {
  height: 100%;
  object-fit: cover;
  text-align: center;
}
</style>
