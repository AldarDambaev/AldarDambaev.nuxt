<template>
  <div class="home">
    <AppHero class="home__hero"/>

    <AppOffers class="home__offers"/>
    
    <AppAbout class="home__about"/>

    <AppUpcoming class="home__upcoming"/>

    <AppListing 
    v-slot="{list}" 
    :title="'Блог'" 
    class="home__listing"
    :moreLink="true"
    :grid="'column'"
    :url="'http://localhost:3000/json/blog.json'"
    >
    <ArticleCard
        v-for="card in list"
        :key="card.slug"
        :data="card"
        class="app-listing__card"
      />
    </AppListing>
  </div>
</template>

<script setup></script>

<style lang="less">
.home {
  box-sizing: border-box;
  width: 100%;
  padding: 100px 0;
  overflow: hidden;
  @media @bw1340 {
    padding: 80px 0;    
  }
  &__hero {
    margin-bottom: 100px;
    @media @bw768 {
      margin-bottom: 75px;
    }
  }
  &__offers {
    margin: 0 auto 200px;
    @media @bw1340 {
      margin-bottom: 130px;
    }
    @media @bw768 {
      margin-bottom: 100px;
    }
  }
  &__container {
    .container;
  }
  &__about {
    margin-bottom: 90px;
  }
  &__upcoming {
    margin-bottom: 65px;
  }
  &__listing {
    margin-bottom: 95px;
  }
  &__contacts {
    margin-bottom: 150px;
    @media @bw1660 {
      margin-bottom: 130px;
    }
    @media @bw1340 {
      margin-bottom: 120px;
    }
  }
}
</style>