<script setup lang="ts">
const { decodeURI } = useHelpers();
const { node } = defineProps({
  node: { type: Object, required: true },
});
</script>

<template>
  <NuxtLink :to="`/product-category/${decodeURI(node.slug)}`" class="relative flex justify-center overflow-hidden border border-white rounded-xl item snap-mandatory snap-x">
    <NuxtImg
      v-if="node.image?.sourceUrl"
      width="220"
      height="280"
      class="absolute inset-0 object-cover w-full h-full"
      :src="node.image?.sourceUrl"
      :alt="node.image?.altText || node.name"
      :title="node.image?.title || node.name"
      loading="lazy"
      fit="outside"
      format="webp"
      densities="x1 x2" />
    <img
      v-else
      src="/images/placeholder.jpg"
      :alt="node.image?.altText || node.name"
      :title="node.image?.title || node.name"
      class="absolute inset-0 object-cover w-full h-full"
      width="220"
      height="280"
      loading="lazy" />
    <div class="absolute inset-x-0 bottom-0 opacity-50 bg-gradient-to-t from-black to-transparent h-1/2"></div>
    <span class="relative z-10 mt-auto mb-2 text-sm font-semibold text-white capitalize md:text-base md:mb-4">{{ node.name }}</span>
  </NuxtLink>
</template>

<style lang="postcss" scoped>
.item {
  scroll-snap-align: start;
  scroll-snap-stop: always;
  aspect-ratio: 4 / 5;
}
</style>
