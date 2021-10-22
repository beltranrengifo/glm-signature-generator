<template>
  <span
    class="copy__button"
    :class="{'active': isCopied}"
    :data-clipboard-target="elementToCopy">
    {{ text }}
  </span>
</template>

<script>
import Clipboard from 'clipboard'

export default {
  name: 'CopyButton',
  data() {
    return {
      clipboardInstance: null,
      isCopied: false,
      text: 'copiar',
    }
  },
  props: {
    elementToCopy: {
      type: String,
      required: true,
    },
  },
  mounted() {
    this.clipboardInstance = new Clipboard('.copy__button')
    this.clipboardInstance.on('success', e => {
      this.text = 'copiado'
      this.isCopied = true
      setTimeout(() => {
        this.isCopied = false
        this.text = 'copiar'
        e.clearSelection()
      }, 1500)
    })
  },
}
</script>

<style lang="scss" scoped>
  .copy__button {
    position: relative;
    text-transform: uppercase;
    font-size: 12px;
    color: $--color-info;
    background: $--color-white;
    border: 1px solid $--color-info;
    padding: 8px 20px;
    border-radius: 4px;
    cursor: pointer;
    transition: all .2s;
    font-weight: 600;
    &:hover {
      color: $--color-white;
      background: $--color-info;
    }
    &.active {
      color: $--color-white;
      border-color: $--color-success;
      background: $--color-success;
    }
  }
</style>
