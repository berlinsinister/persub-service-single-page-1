<template>
  <div class="options-container">
    <div class="border" :style="{ border: border }"></div>
    <div class="info">
      <div class="title-and-subtitle">
        <div class="title">{{ title }}</div>
        <div class="subtitle">1 ლიტრი</div>
      </div>
      <div class="controls">
        <div class="add-and-remove">
          <button @click="removeHandler" class="btn remove">-</button>
          <span class="cart">{{ cart }}</span>
          <button @click="addHandler" class="btn add">+</button>
        </div>
        <div class="price">{{ totalPrice }}ლ</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Options",
  props: {
    title: String,
    border: String,
    price: Number,
  },
  data() {
    return {
      cart: 0,
    };
  },
  methods: {
    addHandler() {
      this.cart++;
    },
    removeHandler() {
      if (this.cart) {
        this.cart--;
      }
    },
  },
  computed: {
    totalPrice() {
      return this.cart === 0 ? this.price : this.price * this.cart;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.options-container {
  //   border: 1px solid blue;
  display: flex;
  width: 70rem;
  height: 5rem;
  border: 1px solid transparent;
  transition: $transition-time ease-out;
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
    //   border: 1px solid red;
    width: 61rem;
    display: flex;
    margin: 0 2rem;
    justify-content: space-between;
    color: #496d7d;
    font-family: "DejaVu Sans Condensed", sans-serif;
    & .title-and-subtitle {
      //   border: 1px solid lime;
      & .title,
      & .subtitle {
        padding: 0.2rem 0;
      }
      & .title {
        font-size: 1.6rem;
      }
      & .subtitle {
        font-size: 1.2rem;
      }
    }
    & .controls {
      // border: 1px solid red;
      width: 17rem;
      font-weight: 600;
      @include flex-space-between;
      & .add-and-remove {
        // border: 1px solid green;
        & .btn {
          $size: 2.5rem;
          width: $size;
          height: $size;
          border: none;
          border-radius: 0.5rem;
          background: #e7e7e7;
          color: #7e98a4;
          font-size: 1.6rem;
          &:focus {
            outline: none;
          }
          &:hover {
            cursor: pointer;
          }
        }
        & .add {
          background: linear-gradient(0deg, #56bd99, #9cdf77);
          color: white;
          &:hover {
            background: linear-gradient(180deg, #56bd99, #9cdf77);
          }
        }
        & .remove {
          &:hover {
            background: linear-gradient(0deg, #ec5f8c, #eb497a);
            color: white;
          }
        }
        & .cart {
          padding: 0 1.5rem;
        }
      }
    }
  }
}

@media (max-width: 850px) {
  .options-container {
    // border: 1px solid blue;
    width: 28rem;
    height: 5rem;
    @include flex-space-between;
    & .info {
      // border: 1px solid red;
      width: 22rem;
      display: flex;
      justify-content: space-between;
      margin: 0; // 1rem;
      .title-and-subtitle {
        //   border: 1px solid lime;
        & .title,
        & .subtitle {
          padding: 0; // 0.2rem 0;
        }
        & .title {
          font-size: 1.4rem;
        }
        & .subtitle {
          font-size: 1.2rem;
        }
      }
      & .controls {
        // border: 1px solid red;
        width: 10rem;
        font-weight: 500;
        font-size: 1.2rem;
        @include flex-space-between;
        & .add-and-remove {
          // border: 1px solid green;
          & .btn {
            $size: 2rem;
            width: $size;
            height: $size;
          }
          & .cart {
            padding: 0 0.8rem;
          }
        }
      }
    }
  }
}
</style>