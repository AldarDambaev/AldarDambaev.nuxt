<template>
  <div class="events">
    <AppListing 
    v-slot="{list}" 
    :title="Мероприятия" 
    class="events__listing"
    :moreBtn="true"
    :url="'http://localhost:3000/json/events.json'"
    >
      <EventCard
        v-for="(card, index) in list"
        :key="index"
        :data="card"
        class="app-listing__card"
      />
    </AppListing>
  </div>
</template>

<script setup>

</script>

<style lang="less">
  .events {
    /* Стили добавьте самостоятельно */
  }
</style>