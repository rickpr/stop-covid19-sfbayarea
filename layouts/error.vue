<template>
  <div class="Error">
    <h1 class="Error-Heading">
      {{ headingTitle }}
    </h1>
    <div class="Error-BodyContainer">
      <p class="Error-Body">
        This page has not been prepared yet.
      </p>
      <div class="Error-ButtonContainer">
        <NuxtLink to="/" class="Error-Button">
          TOP
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  computed: {
    isNotFound(): boolean {
      return this.error.statusCode === 404
    },
    headingTitle(): string {
      return this.isNotFound ? 'Opps...Page Not Found.' : 'Error'
    }
  }
})
</script>

<style lang="scss" scoped>
.Error {
  &-Heading {
    @include font-size(30);
    color: $gray-2;
    font-weight: normal;
    margin-top: 28px;
    @include lessThan($small) {
      margin-top: 12px;
    }
  }
  &-BodyContainer {
    margin-top: 12px;
    @include card-container();
    padding: 20px;
  }
  &-Body {
    @include body-text();
  }
  &-ButtonContainer {
    margin-top: 24px;
    text-align: center;
  }
  &-Button {
    @include button-text('md');
    text-decoration: none;
    max-width: 300px;
    width: 100%;
    font-weight: bold;
  }
}
</style>
