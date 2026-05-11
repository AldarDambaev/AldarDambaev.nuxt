<template>
  <article class="event">
    <header class="event__header">
      <h1 class="event__title title">{{ data.title }}</h1>

      <div class="event__about">
        <div class="event__info">
          <div class="event__border"></div>

          <time v-if="datetime" :datetime="data.date" class="event__time">
            {{ datetime.date }}
          </time>
          <div class="event__info-text">{{ data.location }}</div>
          
          <div class="event__border"></div>
        </div>

        <picture class="event__picture">
          <source type="image/webp" :srcset="data.img_webp" />

          <img :src="data.img" :alt="data.alt" class="event__image" />
        </picture>

        <div class="event__info">
          <div class="event__border-after"></div>
          <span v-if="datetime" class="event__time" data-caption="начало">
            {{ datetime.time }}
          </span>
          <div class="event__info-text">{{ data.address }}</div>
          <div class="event__border-after"></div>
        </div>
      </div>
    </header>

    <div class="event__container">
      <div class="content event__content" v-html="data.content"></div>
    </div>
  </article>
</template>

<script setup>
  const slug = computed(() => useRoute().params.event);
  const URL = computed(
    () => `http://localhost:3000/json/events/${slug.value}.json`,
  );

  const { data } = await useFetch(URL);

  const datetime = computed(() => {
    try {
      const date = new Date(data.value.date);
      return {
        date: date.toLocaleDateString(),
        time: date.toLocaleTimeString("ru-RU", {
          hour: "2-digit",
          minute: "2-digit",
        }),
      };
    } catch {
      return null;
    }
  });
</script>

<style lang="less">

.event {
    padding: 40px 0 150px;
    padding-left: 80px;
    @media @bw768 {
        padding: 40px 0 150px;
    }

    &__header {
      display: flex;
      flex-direction: column;

    }
    &__about {
      display: flex;
      flex-direction: row;
      gap: 50px;
      margin-top: 50px;
      text-align: center;
      align-items: center;
      justify-content: center;
      font-family: Lora;
      font-size: 50px;
      @media @bw768{
        font-size: 30px;
      }
    }
    &__title{
    margin-left: 490px;
    width: 819px;
    height: 90px;
    display: flex;
    justify-content: center;
    font: 70px Lora;
    @media @bw768 {
      margin-left: 40px;
            width: 468px;
            height: 51px;
            padding-left: 0;
            font: 40px Lora;
        }
    }

    &__border {
  display: flex;
  margin-bottom: 60px;
  margin-top: 60px;
  
  &::before {
    content: "";
    flex-grow: 1;
    width: 2px;
    height: 2px;
    margin-right: 50px;
    background: linear-gradient(
      270deg,
      #1c1b1b 0%,
      rgba(255, 255, 255, 0) 82.86%
    );
    
    @media @bw1660 {
      margin-right: 45px;
    }
    @media @bw1340 {
      margin-right: 25px;
    }
    @media @bw768 {
      margin-right: 10px;
    }
  }
}
&__border-after{
  display: flex;
  margin-bottom: 60px;
  margin-top: 60px;
  &::after {
        content: "";
        flex-grow: 1;
        width: 2px;
        height: 2px;
      }
      &::after {
        margin-left: 50px;
        background: linear-gradient(
          90deg,
          #1c1b1b 0%,
          rgba(255, 255, 255, 0) 82.86%
        );
        @media @bw1660 {
          margin-left: 45px;
        }
        @media @bw1340 {
          margin-left: 25px;
        }
        @media @bw768 {
          margin-left: 10px;
        }
      }
}
}




</style>