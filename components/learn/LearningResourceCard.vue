<template>
  <article class="learning-resource-card">
    <img
      class="learning-resource-card__image"
      alt=""
      src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="
      :lazy-background="image"
    >
    <div class="learning-resource-card__content">
      <h3 class="copy__subtitle">
        {{ title }}
      </h3>
      <slot />
      <AppCta class="copy__link" :url="to">
        {{ ctaLabel }}
      </AppCta>
    </div>
  </article>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator'
import AppCta from '~/components/ui/AppCta.vue'

@Component({
  components: { AppCta }
})
export default class extends Vue {
  @Prop(String) image!: any
  @Prop(String) title!: any
  @Prop(String) ctaLabel!: any
  @Prop(String) to!: any
}
</script>

<style lang="scss" scoped>
@import '~/assets/scss/blocks/copy.scss';
@import '~carbon-components/scss/globals/scss/typography';

.learning-resource-card {
  height: 13rem;
  width: 100%;
  background-color: $cool-gray-10;
  display: flex;

  @include mq($until: medium) {
    height: auto;
    flex-direction: column;
  }

  &__image {
    width: 14rem;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    overflow: hidden;

    @include mq($from: medium, $until: large) {
      width: 13rem;
    }

    @include mq($until: medium) {
      height: 11rem;
      width: auto;
    }
  }

  &__content {
    flex: 1;
    margin: 1rem;
    display: flex;
    flex-direction: column;
  }
}
</style>
