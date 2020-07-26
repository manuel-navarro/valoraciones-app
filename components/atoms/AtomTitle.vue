<template>
  <component :is="tag" class="text-3xl pb-2 font-bold text-green-600">{{
    content
  }}</component>
</template>

<script>
export default {
  name: 'AtomTitle',
  props: ['tag', 'content'],
}
</script>
<style>
/* TODO: Use tailwind classes instead */
h1 {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-size: 100px;
  letter-spacing: 1px;
}
</style>
