<template>
  <div class="container">
    <div class="service-title">შერჩეული პროდუქტები</div>
    <div class="chosen-products-container">
      <div v-for="(detail, index) in singleChosenProductDetails" :key="index">
        <SingleChosenProduct
          :url="detail.url"
          :title="detail.title"
          :weight="detail.weight"
          :price="detail.price"
        />
      </div>
    </div>
    <div class="services">
      <div class="delivery">
        <div class="service-title">ვის მოვატანინო</div>
        <div class="delivery-options">
          <button>Wolt</button>
          <button>Glovo</button>
          <button>Elvis</button>
        </div>
      </div>
      <div class="frequency">
        <div class="service-title">რა სიხშირით</div>
        <div class="frequency-options">
          <button>Weekly</button>
          <button>Daily</button>
          <button>Monthly</button>
          <button>Quarterly</button>
        </div>
      </div>
      <div class="subscribe">
        <div class="service-title">გამოწერა</div>
        <div class="subscription-options">
          <div
            v-for="(detail, index) in billingDetails"
            :key="index"
            class="billing"
          >
            <div class="billing-type">{{ detail.type }}</div>
            <div v-show="detail.saving" class="saving">save 2 months</div>
            <div class="billing-price">
              ${{ detail.price }}<span>{{ detail.duration }}</span>
            </div>
          </div>
          <input type="submit" value="Subscribe Now" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SingleChosenProduct from "./SingleChosenProduct.vue";
export default {
  name: "Chosen Products",
  components: { SingleChosenProduct },
  props: {},
  data() {
    return {
      singleChosenProductDetails: [
        {
          url: "apple.png",
          title: "Apple",
          weight: "2kg",
          price: "8",
        },
        {
          url: "peach.png",
          title: "Peach",
          weight: "4kg",
          price: "18",
        },
        {
          url: "watermelon.png",
          title: "Watermelon",
          weight: "1 peace",
          price: "13",
        },
      ],
      billingDetails: [
        {
          type: "Bill monthly",
          price: "39",
          duration: "/month",
          saving: false,
        },
        {
          type: "Bill early",
          price: "390",
          duration: "/year",
          saving: true,
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.container {
  // border: 1px solid rebeccapurple;
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto;
  & > div {
    // border: 1px solid limegreen;
  }
}

.chosen-products-container {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto auto;
  grid-gap: 0.8rem;
  // border: 1px solid blue;
}

.button {
  width: 11rem;
  height: 3.8rem;
  background: white;
  color: black;
  border: none;
  border-radius: 1rem;
  box-shadow: 0px -11px 8px -10px rgba(gray, 0.1),
    0px 11px 8px -10px rgba(gray, 0.1);
  &:focus {
    outline: none;
  }
  &:hover {
    cursor: pointer;
    background: linear-gradient(90deg, #edbdab, #f2aa9c, #f5bb9b);
    color: white;
  }
}

.services {
  // border: 1px solid red;
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  grid-gap: 2rem;
}

.service-title {
  font-size: 1.8rem;
  font-family: "DejaVu Sans Condensed", sans-serif;
  padding: 1.5rem 0;
}

.delivery-options,
.frequency-options {
  display: grid;
  grid-template-columns: repeat(3, auto);
  grid-auto-rows: auto;
  justify-content: space-between;
  & button {
    @extend .button;
  }
}

.frequency-options {
  grid-gap: 2rem;
}

.subscription-options {
  // border: 1px solid red;
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: repeat(3, auto);
  grid-gap: 2rem;
  & .billing {
    // width: 30.6rem; // auto; // 37rem;
    height: 5.5rem;
    background: white;
    border: 2px solid #f5bb9b;
    border-radius: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 3rem;
    position: relative;
    transition: $transition-time ease-out;
    &:hover {
      cursor: pointer;
      transform: translate(2px, 2px);
    }
    & .billing-type,
    & .billing-price {
      font-size: 1.6rem;
      font-weight: 500;
      // border: 2px solid blue;
    }
    & .saving {
      position: absolute;
      left: 11rem;
      background: #f9edc9;
      color: #d6ae47;
      border-radius: 3rem;
      text-transform: uppercase;
      padding: 0.5rem 1rem;
      font-size: 1rem;
    }
    & .billing-price {
      & span {
        font-size: 1.2rem;
        font-weight: 400;
        color: gray;
      }
    }
  }
  & input[type="submit"] {
    height: 5.9rem;
    border: none;
    border-radius: 1rem;
    background: linear-gradient(0deg, #56bd99, #9cdf77);
    color: white;
    font-size: 1.6rem;
    font-weight: 500;
    transition: $transition-time ease-out;
    &:focus {
      outline: none;
    }
    &:hover {
      cursor: pointer;
      background: linear-gradient(180deg, #56bd99, #9cdf77);
    }
  }
}

// MEDIA
@media (max-width: 1600px) {
  .delivery-options,
  .frequency-options {
    grid-template-columns: auto;
    grid-auto-rows: auto;
    grid-gap: 1rem;
    justify-content: start;
  }

  .subscription-options {
    & .billing {
      padding: 0 1.5rem;
      & .billing-type,
      & .billing-price {
        font-size: 1.4rem;
      }
      & .saving {
        display: none;
      }
    }
  }
}

@media (max-width: 1400px) {
  .container {
    grid-template-columns: auto;
    grid-auto-rows: auto;
    grid-gap: 1rem;
    width: 115.3rem;
  }

  .chosen-products-container {
    grid-template-columns: auto auto auto;
    grid-template-rows: auto;
    grid-gap: 1rem;
    // border: 1px solid blue;
    // width: 115.3rem;
  }

  .services {
    grid-template-columns: auto auto auto;
    grid-template-rows: auto;
    grid-gap: 1rem;
  }

  .delivery-options,
  .frequency-options {
    grid-template-columns: auto auto;
    grid-template-rows: auto;
  }

  .service-title {
    font-size: 1.6rem;
  }

  .subscription-options {
    // border: 1px solid green;
    grid-template-columns: repeat(3, auto);
    grid-template-rows: auto;
    grid-gap: 0; // for space between
    justify-content: space-between;
    & .billing {
      width: 17rem;
      padding: 0 1.5rem;
      & .billing-type,
      & .billing-price {
        font-size: 1.4rem;
      }
      & .saving {
        display: none;
      }
    }
    & input[type="submit"] {
      width: 20rem;
    }
  }
}

@media (max-width: 1200px) {
  .container {
    width: 92.3rem;
  }

  .subscription-options {
    grid-template-columns: auto auto;
    grid-template-rows: auto;
    grid-gap: 1rem;
    justify-content: start;
    & .billing {
      width: 17rem;
      height: 3.8rem;
      padding: 0 1rem;
    }
    & input[type="submit"] {
      width: 19.5rem;
      height: 3.4rem; // 3.8rem;
    }
  }
}

@media (max-width: 1000px) {
  .container {
    width: 76rem;
  }

  .button {
    width: 8rem;
  }
}

@media (max-width: 850px) {
  .container {
    width: 32rem;
  }

  .chosen-products-container,
  .services {
    grid-template-columns: auto;
    grid-auto-rows: auto;
  }

  .service-title {
    font-size: 1.4rem;
    padding: 0.7rem 0;
  }

  .delivery-options,
  .frequency-options {
    grid-template-columns: repeat(3, auto);
    grid-template-rows: auto;
  }

  .subscription-options {
    grid-template-columns: auto;
    grid-auto-rows: auto;
    & .billing {
      width: 29.6rem;
    }
    & input[type="submit"] {
      width: 32rem;
    }
  }
}
</style>