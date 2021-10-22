<template>
  <div class="app-title">
    <component :is="tag" class="app-title__title">
      <small class="app-title__subtitle">{{ subtitle }}</small>
      {{ title }}
    </component>
  </div>
</template>

<script>
export default {
  name: 'AppTitle',
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
    },
    tag: {
      type: String,
      default: 'h2',
    },
  },
}
</script>

<style lang="scss" scoped>
.app-title {
  &__title {
    font-size: 24px;
    font-family: $--font-serif;
    margin-bottom: 16px;
    font-weight: initial;
  }
  &__subtitle {
    font-weight: initial;
    font-size: 12px;
    font-family: $--font-sans;
    display: block;
    margin-bottom: 8px;
  }
}
</style>
