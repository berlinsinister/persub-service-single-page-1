<template>
  <div class="service-provider-container">
    <div class="service-provider-photo">
      <img src="../assets/images/profile.jpg" alt="profile" />
      <div class="status"></div>
    </div>
    <div class="service-provider-info">
      <div class="name-and-location">
        <div class="name">Beka Kvartskhava</div>
        <div class="location">Tbilisi, Georgia</div>
      </div>
      <div class="position-and-rating">
        <button class="position">Expert</button>
        <div class="rating">4 reviews</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Service Provider",
  props: {},
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.service-provider-container {
  // border: 1px solid crimson;
  width: 70rem;
  display: grid;
  grid-template-columns: auto auto;
  grid-template-rows: auto;
  padding: 1.5rem 0;
  & .service-provider-photo {
    position: relative;
    & img {
      $img-size: 6.8rem;
      width: $img-size;
      height: $img-size;
      object-fit: cover;
      border: 2px solid white;
      border-radius: 50%;
      box-shadow: 0 5px 10px -1px rgba(black, 0.2);
    }
    & .status {
      $status-size: 1.7rem;
      position: absolute;
      top: 5rem;
      left: 5rem;
      width: $status-size;
      height: $status-size;
      background: #74c299;
      border-radius: 50%;
      border: 2px solid white;
    }
  }
  .service-provider-info {
    width: 60rem;
    // border: 1px solid royalblue;
    display: grid;
    grid-template-columns: auto auto;
    grid-template-rows: auto;
    & .name-and-location {
      & .name,
      & .location {
        padding: 0.3rem 0;
      }
      & .name {
        font-size: 1.6em;
      }
      & .location {
        font-size: 1.4rem;
        font-style: italic;
      }
    }
    & .position-and-rating {
      align-self: center;
      justify-self: end;
      & .position {
        width: 8rem;
        padding: 0.5rem 0;
        background: white;
        color: #2f5371;
        border-radius: 0.2rem;
        border: 1px solid #2f5371;
        font-size: 1.4rem;
        font-weight: 600;
        margin-bottom: 0.7rem;
        &:focus {
          outline: none;
        }
      }
      & .rating {
        text-align: center;
        font-weight: 500;
      }
    }
  }
}

@media (max-width: 850px) {
  .service-provider-container {
    // border: 1px solid crimson;
    width: 26rem; // 70rem;
    padding: 1rem 0;
    grid-template-columns: auto;
    grid-template-rows: auto;
    justify-content: center;
    grid-gap: 1rem;
    .service-provider-info {
      // border: 1px solid royalblue;
      width: 28rem;
      & .name-and-location {
        & .name {
          font-size: 1.4em;
        }
      }
      & .position-and-rating {
        & .position {
          width: 7rem;
          font-size: 1.3rem;
          font-weight: 500;
        }
        & .rating {
          text-align: right;
        }
      }
    }
  }
}
</style>