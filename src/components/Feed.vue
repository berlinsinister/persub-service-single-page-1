<template>
  <div class="feed-container">
    <div class="feed-image">
      <img :src="require('../assets/images/' + url)" alt="feed content" />
      <div class="linear-gradient-black"></div>
      <div class="timing">
        <button
          v-for="(time, index) in timing"
          :key="index"
          @click="addToSubscriptions"
          :value="time"
        >
          {{ time }}
        </button>
      </div>
    </div>
    <div class="content">
      <div class="logo">
        <img :src="require('../assets/images/' + logo)" alt="feed logo" />
        <div class="info">
          <div class="title">{{ title }}</div>
          <div class="description">{{ description }}</div>
        </div>
      </div>
      <div class="list">
        <div v-for="(detail, index) in listDetails" :key="index">
          <List :title="detail.title" :border="detail.border" />
        </div>
      </div>
      <button
        class="see-details"
        :style="{ background: background, color: color }"
      >
        დეტალების ნახვა
      </button>
      <div class="location">Business located in Tbilisi, Georgia</div>
    </div>
  </div>
</template>

<script>
import List from "./List.vue";

export default {
  name: "Feed",
  components: { List },
  props: {
    title: String,
    description: String,
    url: String,
    logo: String,
    background: String,
    color: String,
    index: Number,
  },
  data() {
    return {
      timing: ["Weekly", "Monthly", "Yearly"],
      listDetails: [
        {
          title: "ჟუჟუნა კენკრის",
          border: "1px solid #7f6868",
        },
        {
          title: "ჟუჟუნა ჟოლოს",
          border: "1px solid #c66f6c",
        },
        {
          title: "ჟუჟუნა ბანანის",
          border: "1px solid #d4d278",
        },
        {
          title: "ჟუჟუნა კენკრის",
          border: "1px solid #7f6868",
        },
        {
          title: "ჟუჟუნა ჟოლოს",
          border: "1px solid #c66f6c",
        },
        {
          title: "ჟუჟუნა ბანანის",
          border: "1px solid #d4d278",
        },
        {
          title: "ჟუჟუნა კენკრის",
          border: "1px solid #7f6868",
        },
        {
          title: "ჟუჟუნა ჟოლოს",
          border: "1px solid #c66f6c",
        },
        {
          title: "ჟუჟუნა ბანანის",
          border: "1px solid #d4d278",
        },
        {
          title: "ჟუჟუნა კენკრის",
          border: "1px solid #7f6868",
        },
        {
          title: "ჟუჟუნა ჟოლოს",
          border: "1px solid #c66f6c",
        },
        {
          title: "ჟუჟუნა ბანანის",
          border: "1px solid #d4d278",
        },
      ],
    };
  },
  methods: {
    addToSubscriptions(event) {
      let timing = event.target.value;
      let subscriptionsDetails = {
        timing: timing,
        title: this.title,
        logo: this.logo,
      };
      this.$emit("addToSubscriptions", subscriptionsDetails);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.feed-container {
  width: 76rem;
  height: 52rem;
  display: grid;
  grid-template-columns: auto auto;
  grid-auto-rows: auto;
  & .feed-image,
  & .content {
    width: 38rem;
    position: relative;
  }
}

.feed-image {
  & img,
  & .linear-gradient-black {
    width: 38rem;
    border-radius: 1.5rem;
  }
  & img {
    height: 52rem;
    object-fit: cover;
    transition: $transition-time ease-out;
    &:hover {
      filter: brightness(1.1);
    }
  }
  & .linear-gradient-black {
    position: absolute;
    bottom: 0.3rem; // for better overlay
    left: 0;
    height: 20rem;
    background: linear-gradient(0deg, rgba(black, 0.5), rgba(black, 0));
  }
  & .timing {
    position: absolute;
    bottom: 3rem;
    left: 2rem;
    display: flex;
    align-items: center;
    & button {
      width: 6rem;
      height: 2.2rem;
      background: transparent;
      color: white;
      border: 1px solid white;
      border-radius: 2px;
      margin: 0 0.5rem;
      opacity: 0.7;
      font: {
        family: Verdana, Tahoma, sans-serif;
        size: 1rem;
      }
      &:focus {
        outline: none;
      }
      &:hover {
        cursor: pointer;
        transform: translate(1px, 1px);
        opacity: 1;
      }
    }
  }
}

.content {
  display: grid;
  grid-template-columns: auto;
  //   grid-template-rows: 8.8rem 39rem auto;
  grid-template-rows: 8.8rem auto auto;
}

.logo {
  // border: 1px solid limegreen;
  padding: 2rem;
  display: flex;
  align-items: center;
  & > div {
    margin-left: 2rem;
    color: #375a77;
  }
  & > div > div {
    padding: 0.2rem 0;
  }
  & .title {
    font-size: 2rem;
    font-weight: 500;
  }
  & .description {
    font-size: 1.2rem;
  }
}

@include scrollbar;

.list {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: repeat(12, auto);
  justify-content: center;
  grid-gap: 1.5rem;
  background: white;
  height: 35rem; //39rem;
  overflow-y: scroll;
  box-shadow: 0px -11px 8px -10px rgba(black, 0.1),
    11px 0px 8px -10px rgba(black, 0.1);
  padding: 2rem 0;
}

.see-details {
  position: absolute;
  bottom: 8rem;
  width: 30rem;
  height: 5rem;
  margin-left: 4rem;
  border-radius: 1.5rem;
  border: none;
  font-family: "DejaVu Sans Condensed", sans-serif;
  font-size: 1.7rem;
  transition: $transition-time ease-out;
  &:hover {
    cursor: pointer;
    filter: brightness(1.05);
    border-radius: 2rem;
  }
}

.location {
  // border: 1px solid crimson;
  height: 4.5rem;
  margin-left: 2rem; /** new */
  display: flex;
  align-items: center;
  font-family: "Trebuchet MS", "Lucida Sans", Arial, sans-serif;
  color: #777777;
}

// MEDIA
@media (max-width: 850px) {
  $smallest-media-width: 32rem;
  .feed-container {
    width: auto; // 32rem;
    height: auto; // 52rem;
    grid-template-columns: auto;
    grid-template-rows: auto auto;
    // border: 1px solid red;
    & .feed-image,
    & .content {
      width: $smallest-media-width;
    }
  }

  .feed-image {
    & img,
    & .linear-gradient-black {
      width: $smallest-media-width;
    }
    & img {
      height: 48rem;
      object-fit: cover;
    }
  }

  .see-details {
    // bottom: 5rem;
    width: $smallest-media-width - 8rem;
  }

  .location {
    margin-left: 0;
  }
}
</style>