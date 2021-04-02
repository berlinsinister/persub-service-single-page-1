<template>
  <div
    class="sidebar-container"
    :class="
      windowWidth <= 1000
        ? index === 0 || index === 3
          ? 'background-beige'
          : 'background-orange'
        : windowWidth <= 1200
        ? index === 0 || index === 3
          ? 'border-left-beige'
          : 'border-left-orange'
        : ''
    "
  >
    <img :src="require('../assets/images/' + url)" alt="sidebar content" />
    <!-- <div
      class="border"
      :style="index === 0 || index === 3 ? beige : orange"
    ></div> -->
    <div
      class="border"
      :class="
        windowWidth >= 1200
          ? index === 0 || index === 3
            ? 'border-beige'
            : 'border-orange'
          : ''
      "
    ></div>
    <div>
      <div class="title">{{ title }}</div>
      <div class="subtitle">
        Bringing family and friends together in support of one another.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  props: {
    title: String,
    index: Number,
    url: String,
  },
  data() {
    return {
      // orange: "border: 2px solid #ee7038",
      // beige: "border: 1px solid #c6bfaf",
      windowWidth: window.innerWidth,
    };
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.border-orange {
  border: 2px solid #ee7038;
}

.border-beige {
  border: 1px solid #c6bfaf;
}

.border-left-orange {
  border-left: 2px solid #ee7038;
}

.border-left-beige {
  border-left: 1px solid #c6bfaf;
}

.background-orange {
  background: #ee7038;
}

.background-beige {
  background: #c6bfaf;
}

.sidebar-container {
  width: 34.2rem;
  height: 10rem;
  display: flex;
  align-items: center;
  position: relative;
  transition: $transition-time ease-out;
  &:hover {
    cursor: pointer;
    & img {
      transform: rotate(0);
    }
    & .border {
      // display: none;
      opacity: 0; // 0.2;
      transform: scale(1.1);
    }
  }
  & img,
  & .border {
    width: 12.9rem;
    height: 9rem;
    border-radius: 1.5rem;
    transition: $transition-time ease-out;
  }
  & img {
    object-fit: cover;
    margin-left: 0.2rem;
    transform: rotate(-2.5deg);
    // border: 1px solid lime;
  }
  & .border {
    position: absolute;
    top: 0.5rem;
    left: 0;
  }
  & .title,
  & .subtitle {
    margin-left: 2rem;
    padding: 0.2rem 0;
  }
  & .title {
    font-size: 1.8rem;
    font-weight: 500;
  }
  & .subtitle {
    font-size: 1.2rem;
  }
}

// MEDIA
@media (max-width: 1200px) {
  .sidebar-container {
    width: auto;
    height: auto;
    padding: 0 1rem;
    // border-left: 1px solid crimson;
    &:hover {
      // opacity: 0.7;
      transform: translateY(3px);
    }
    & img,
    & .border {
      display: none;
    }
    & .title,
    & .subtitle {
      margin-left: 0;
    }
  }
}

@media (max-width: 1000px) {
  .sidebar-container {
    // width: auto;
    // height: auto;
    justify-content: center;
    padding: 1rem;
    border-radius: 0.5rem;
    color: white;
    & .subtitle {
      display: none;
    }
  }
}

@media (max-width: 850px) {
  .sidebar-container {
    & .title {
      font-size: 1.4rem;
    }
  }
}
</style>