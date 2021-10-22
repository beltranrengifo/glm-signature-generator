<template>
  <div :class="{ 'is-folded': folded }" class="instructions__block">
    <h3 class="instructions__title" @click="handleAccordion">
      {{ type }}
      <span class="accordion-trigger">
        <i class="fa fa-angle-down"></i>
      </span>
    </h3>
    <ol class="instructions__list">
      <li
        class="instructions__item"
        v-for="item in content.content"
        :key="item"
        v-html="item"
      ></li>
      <li class="instructions__item" v-for="image in content.images" :key="image">
        <img :src="require(`@/assets/images/${image}`)" alt="image" />
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'InstructionsBlock',
  data() {
    return {
      folded: true,
    }
  },
  props: {
    type: {
      type: String,
    },
    content: {
      type: Object,
      required: true,
    },
  },
  methods: {
    handleAccordion() {
      this.folded = !this.folded
    },
  },
}
</script>

<style lang="scss" scoped>
.instructions {
  &__title {
    border-bottom: 1px solid $--color-grey-dark;
    padding-bottom: 4px;
    color: $--color-grey-dark;
    display: flex;
    justify-content: space-between;
    padding-right: 16px;
    padding-left: 16px;
    cursor: pointer;
    transition: color 0.2s;
    margin-bottom: 4px;
    &:hover {
      color: black;
    }
  }
  &__list {
    overflow: hidden;
    height: auto;
    max-height: 600px;
    transition: max-height 0.4s;
    margin: 0;
  }
  &__item {
    line-height: 1.75;
  }
  &__block {
    overflow: hidden;
    padding: 24px 24px 0;
    box-sizing: border-box;
    &.is-folded {
      ol {
        max-height: 0;
      }
    }
    &:not(.is-folded) {
      .instructions__title {
        color: black;
      }
    }
    &:last-child {
      padding-bottom: 32px;
    }
  }
}
.accordion-trigger {
  font-size: 24px;
}
</style>
