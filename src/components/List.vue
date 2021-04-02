<template>
  <div class="list-container">
    <div class="border" :style="{ border: border }"></div>
    <div class="info">
      <div>
        <div class="title">{{ title }}</div>
        <div class="subtitle">1 ლიტრი</div>
      </div>
      <div class="price">15₾</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "List",
  props: {
    title: String,
    border: String,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.list-container {
  // border: 1px solid blue;
  @include flex-space-between;
  width: 34rem;
  height: 5rem;
  &:hover {
    cursor: pointer;
    & > .border {
      border-radius: 1rem;
    }
  }
  & .border {
    width: 5rem;
    height: 5rem;
    border-radius: 0.5rem;
    transition: $transition-time ease-out;
  }
  & .info {
    width: 25rem;
    display: flex;
    margin: 0 2rem;
    justify-content: space-between;
    color: #7e98a4;
    font-family: "DejaVu Sans Condensed", sans-serif;
    & > div > div {
      padding: 0.2rem 0;
    }
    & .title,
    & .price {
      font-size: 1.6rem;
    }
    & .subtitle {
      font-size: 1.2rem;
    }
  }
}

@media (max-width: 850px) {
  .list-container {
    width: 28rem;
    height: 5rem;
    & .border {
      width: 5rem;
      height: 5rem;
    }
    & .info {
      width: 21rem;
      margin: 0;
    }
  }
}
</style>