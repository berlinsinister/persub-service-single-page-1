<template>
  <div class="single-chosen-product-container">
    <img
      :src="require('../assets/images/' + url)"
      alt="single chosen product"
    />
    <div class="info">
      <div>
        <div class="title">{{ title }}</div>
        <div class="weight">{{ weight }}</div>
      </div>
      <div class="price">${{ price }}</div>
    </div>
    <div class="close"><span>x</span></div>
  </div>
</template>

<script>
export default {
  name: "Single Chosen Product",
  props: {
    url: String,
    title: String,
    weight: String,
    price: Number,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.single-chosen-product-container {
  width: auto; // 37rem;
  height: 8.8rem;
  position: relative;
  @include flex-space-between;
  background: white;
  border-radius: 1rem;
  box-shadow: 0px -11px 8px -10px rgba(gray, 0.1),
    0px 11px 8px -10px rgba(gray, 0.1);
  //   border: 1px solid hotpink;
  transition: $transition-time ease-out;
  &:hover {
    cursor: pointer;
    transform: translate(2px, 2px);
  }
  & .info {
    // border: 1px solid green;
    width: 22rem;
    display: grid;
    grid-template-columns: auto auto;
    grid-template-rows: auto;
    color: black;
    & > div > div {
      padding: 0.2rem 0;
    }
    & .title {
      font-size: 1.8rem;
      font-weight: 500;
    }
    & .weight {
      font-size: 1.2rem;
    }
    & .price {
      font-size: 2rem;
      font-weight: 500;
      align-self: center;
      justify-self: end;
    }
  }
  & .close {
    width: 3.5rem;
    height: inherit;
    background: #e7e7e7;
    color: white;
    @include flex-centered-totally;
    border-top-right-radius: 1rem;
    border-bottom-right-radius: 1rem;
    transition: $transition-time ease-out;
    & span {
      font-size: 1.6rem;
      transition: 0.2s ease-out;
    }
    &:hover {
      background: #f1aa9b;
      & span {
        transform: rotate(360deg);
      }
    }
  }
}

@media (max-width: 1600px) {
  .single-chosen-product-container {
    width: auto; // 37rem;
    height: 7rem; // 8.8rem;
    & img {
      display: none;
    }
    & .info {
      // border: 1px solid blue;
      width: 11rem;
      margin-left: 1.4rem;
      & .title,
      & .price {
        font-size: 1.4rem;
      }
      & .price {
        align-self: start;
      }
    }
    & .close {
      width: 3rem;
    }
  }
}

@media (max-width: 1400px) {
  .single-chosen-product-container {
    width: auto;
    height: 8.8rem;
    & img {
      display: inline;
    }
    & .info {
      // border: 1px solid blue;
      width: 22rem;
      margin-left: 0; // 1.4rem;
      & .title {
        font-size: 1.8rem;
      }
      & .price {
        font-size: 2rem;
        align-self: center;
      }
      & .close {
        width: 3.5rem;
      }
    }
  }
}

@media (max-width: 1200px) {
  .single-chosen-product-container {
    & .info {
      // border: 1px solid blue;
      width: 15rem; // 22rem;
    }
  }
}

@media (max-width: 1000px) {
  .single-chosen-product-container {
    // width: auto; // 37rem;
    height: 7rem; // 8.8rem;
    & img {
      display: none;
    }
    & .info {
      // border: 1px solid blue;
      width: 17rem;
      margin-left: 2.2rem;
      & .title,
      & .price {
        font-size: 1.4rem;
      }
      & .price {
        align-self: start;
      }
    }
    & .close {
      width: 3rem;
    }
  }
}

@media (max-width: 850px) {
  .single-chosen-product-container {
    height: 7rem; // 8.8rem;
    & img {
      width: 7rem;
      height: 7rem;
      object-fit: cover;
      display: inline;
    }
    & .info {
      width: 17rem;
      margin-left: 0; // 2.2rem;
    }
  }
}
</style>