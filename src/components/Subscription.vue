<template>
  <div
    class="subscription-container"
    @mouseover="close = true"
    @mouseleave="close = false"
  >
    <div class="logo">
      <img :src="require('../assets/images/' + details.logo)" alt="logo" />
    </div>
    <div class="info">
      <div>
        <div class="title">{{ details.title }}</div>
        <div class="date">{{ calcDate }}</div>
      </div>
      <div class="timing">{{ details.timing }}</div>
    </div>
    <div v-show="close" class="close" @click="cancelSubscription">&times;</div>
  </div>
</template>

<script>
export default {
  name: "Subscription",
  props: {
    details: Object,
  },
  data() {
    return {
      close: false,
      day: new Date().getDate(),
      month: new Date().getMonth(),
      hours: new Date().getHours(),
      minutes: new Date().getMinutes(),
      months: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ],
    };
  },
  methods: {
    cancelSubscription() {
      this.$emit("cancelSubscription");
    },
  },
  computed: {
    calcDate() {
      let ampm = this.hours > 12 ? "pm" : "am";
      let minutes = this.minutes <= 9 ? "0" + this.minutes : this.minutes;
      return `${this.months[this.month]} ${this.day}, ${
        this.hours
      }:${minutes} ${ampm}`;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.subscription-container {
  //   border: 1px solid hotpink;
  position: relative;
  width: auto; // 37rem;
  height: 8.8rem;
  @include flex-space-between;
  padding: 0 2rem;
  background: white;
  box-shadow: 0px -11px 8px -10px rgba(gray, 0.1),
    0px 11px 8px -10px rgba(gray, 0.1);
  &:hover {
    cursor: pointer;
  }
  & .info {
    width: 25rem;
    display: grid;
    grid-template-columns: auto auto;
    grid-template-rows: auto;
    & > div > div {
      padding: 0.2rem 0;
    }
    & .title {
      font-size: 1.6rem;
      font-weight: 500;
    }
    & .date {
      font-size: 1.2rem;
      color: gray;
    }
    & .timing {
      font-size: 1.6rem;
      align-self: center;
      justify-self: end;
      color: gray;
    }
  }
}

.close {
  $size: 2.5rem;
  position: absolute;
  top: -$size / 2;
  right: -$size / 2;
  width: $size;
  height: $size;
  @include flex-centered-totally;
  background: salmon;
  color: white;
  border-radius: 50%;
}

@media (max-width: 1600px) {
  .subscription-container {
    padding: 0.5rem 2rem;
    & .logo {
      display: none;
    }
    & .info {
      width: auto; // 25rem;
      grid-template-columns: auto;
      grid-auto-rows: auto;
      & div {
        padding: 0.4rem 0;
      }
      & .timing {
        align-self: center;
        justify-self: start;
        color: gray;
      }
    }
  }
}

@media (max-width: 1400px) {
  .subscription-container {
    width: auto; // 37rem;
    height: auto;
    background: white;
    // border: 1px solid red;
    & .info {
      //   border: 1px solid chartreuse;
      width: 25rem;
      display: grid;
      grid-template-columns: auto auto;
      grid-template-rows: auto;
      & .timing {
        justify-self: end;
      }
    }
  }
}
</style>