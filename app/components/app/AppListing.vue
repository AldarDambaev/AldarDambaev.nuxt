<template>
  <section class="app-listing">
    <h1 class="app-listing__title section-title">{{ title }}</h1>

    <div class="app-listing__list">
      <slot />
    </div>

    <button type="button" class="more-btn app-listing__more-btn">
      Показать всё

      <SvgIcon
        class="more-btn__arrow"
        name="arrow_down"
        width="62"
        height="92"
      />
    </button>
  </section>
</template>

<script setup>
  const props = defineProps({
    title: {
      type: String,
      default: "",
    },
  });
</script>

<style lang="less">
  .app-listing {
    box-sizing: border-box;
    width: 100%;
    max-width: 1440px;
    margin: 0 auto;
    padding: 0 40px;

    @media @bw1340 {
      padding: 0 30px;
    }

    @media @bw768 {
      padding: 0 20px;
    }

    &__list {
      display: flex;
      flex-wrap: wrap;
      gap: 58px;
      justify-content: center;
      margin-bottom: 130px;

      @media @bw1660 {
        gap: 40px;
      }

      @media @bw768 {
        gap: 30px;
        margin-bottom: 80px;
      }
    }


  
  }
</style>