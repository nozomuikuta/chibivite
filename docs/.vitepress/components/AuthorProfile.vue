<script setup lang="ts">
import { VPTeamMembers } from 'vitepress/theme'

const { locale = 'en' } = defineProps<{
  locale?: 'en' | 'ja'
}>()

const author = {
  avatar: 'https://avatars.githubusercontent.com/u/16436160',
  name: 'Nozomu Ikuta',
  sponsor: 'https://github.com/sponsors/nozomuikuta',
  links: [
    { icon: 'github', link: 'https://github.com/nozomuikuta' },
    { icon: 'twitter', link: 'https://twitter.com/nozomuikuta' },
  ],
  ...{
    en: {
      desc: 'UnJS Member / Vue.js JP Core Staff / Vite Contributor',
      actionText: 'Sponsor',
    },
    ja: {
      desc: 'UnJSメンバー / Vue.js JP コアスタッフ / Vite コントリビューター',
      actionText: 'スポンサー',
    },
  }[locale],
}
</script>

<template>
  <VPTeamMembers size="small" :members="[author]" id="author-profile" />
</template>

<style scoped>
#author-profile {
  width: 100%;
}

#author-profile :deep(.container) {
  grid-template-columns: 1fr;
  max-width: none !important;
}
</style>
