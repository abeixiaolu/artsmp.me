<script lang="ts" setup>
import type { ContentData } from 'vitepress'

const props = defineProps<{
  post: ContentData
}>()

const date = computed(() =>
  props.post.frontmatter.date.split('T')[0].split('-').slice(1).join('-'),
)
</script>

<template>
  <div class="flex items-center justify-between gap-2 min-w-0">
    <div class="flex items-center gap-2 relative">
      <a :href="post.url" class="truncate hover:underline underline-offset-4 hover:text-primary transition-all duration-200 ease-linear">
        {{ post.frontmatter.title }}
      </a>
      <IconTag v-if="post.frontmatter.series" class="text-sm lg:absolute uppercase left-[-60px] text-primary bg-primary/15" text="Series" />
    </div>
    <span class="text-sm text-[#888A]">
      {{ date }}
    </span>
  </div>
</template>
