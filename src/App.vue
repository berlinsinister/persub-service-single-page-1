<template>
  <Header />
  <main>
    <div class="sidebar">
      <div v-for="(detail, index) in sidebarDetails" :key="index">
        <Sidebar :title="detail.title" :url="detail.url" :index="index" />
      </div>
    </div>
    <div class="feed">
      <SingleService
        :title="singleServiceDetails.title"
        :description="singleServiceDetails.description"
        :url="singleServiceDetails.url"
        :subscribers="singleServiceDetails.subscribers"
        :comments="singleServiceDetails.comments"
      />
      <div v-for="(detail, index) in feedDetails" :key="index">
        <Feed
          :title="detail.title"
          :description="detail.description"
          :url="detail.url"
          :logo="detail.logo"
          :background="detail.background"
          :color="detail.color"
          :index="index"
          @addToSubscriptions="addToSubscriptions"
        />
      </div>
    </div>
    <div class="chosen-products">
      <ChosenProducts />
    </div>
  </main>
</template>

<script>
import Header from "./components/Header.vue";
import Sidebar from "./components/Sidebar.vue";
import Feed from "./components/Feed.vue";
import SingleService from "./components/SingleService.vue";
import ChosenProducts from "./components/ChosenProducts.vue";

export default {
  name: "App",
  components: { Header, Sidebar, SingleService, Feed, ChosenProducts },
  data() {
    return {
      sidebarDetails: [
        {
          title: "Beauty & care",
          url: "image-2.png",
        },
        {
          title: "Transportation",
          url: "image-3.png",
        },
        {
          title: "Family & Friends",
          url: "image-1.png",
        },
        {
          title: "Office & Work",
          url: "image-2.png",
        },
        {
          title: "House Cleaning",
          url: "image-3.png",
        },
        {
          title: "Cars Services",
          url: "image-1.png",
        },
      ],
      singleServiceDetails: {
        title: "ჟუჟუნა",
        description: "ალკოჰოლური სასმელი",
        url: "single-service-image-1.png",
        subscribers: 23,
        comments: 22,
      },
      feedDetails: [
        {
          title: "Jujuna",
          description: "Sparkle Wine",
          url: "feed-image-1.png",
          logo: "feed-logo-1.png",
          background: "linear-gradient(90deg, #edbdab, #f2aa9c, #f5bb9b)",
          color: "white",
        },
        {
          title: "Terminal",
          description: "Co-Working Spaces",
          url: "feed-image-2.png",
          logo: "feed-logo-2.png",
          background: "#f1f2f6",
          color: "black",
        },
        {
          title: "Rezo Wash",
          description: "Househand",
          url: "feed-image-3.png",
          logo: "feed-logo-1.png",
          background: "linear-gradient(90deg, #edbdab, #f2aa9c, #f5bb9b)",
          color: "white",
        },
        {
          title: "Jujuna",
          description: "Sparkle Wine",
          url: "feed-image-1.png",
          logo: "feed-logo-1.png",
          background: "#5172f6",
          color: "white",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style lang="scss">
@import "./assets/sass/vars";
@import "./assets/sass/mixins";

:root {
  font-size: $font-size;
}

html,
body {
  @include reset;
}

body {
  font: {
    family: $font-family;
    size: 1.4rem;
    weight: 400;
  }
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #f8f8f8;
}

main {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-template-rows: auto;
  justify-content: center;
  grid-gap: 2.3rem;
  margin: 13rem 0 3rem 0;
  & > div {
    // border: 1px solid royalblue;
  }
}

.sidebar {
  width: 37rem;
  height: 0; // ????
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  grid-gap: 2.4rem;
  & > div {
    // border: 1px solid green;
  }
}

.feed {
  width: 76rem;
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  grid-gap: 2.4rem;
}

.chosen-products {
  width: 37rem;
  height: 0; // 10rem; // 0;
  // border: 1px solid lime;
  // & > :first-child {
  //   font: {
  //     size: 2rem;
  //     weight: 500;
  //   }
  // }
  // & > :nth-child(2) {
  //   margin-top: 3rem;
  // }
}

// MEDIA
@media (max-width: 1600px) {
  .chosen-products {
    width: 17rem;
  }
}

@media (max-width: 1400px) {
  main {
    grid-template-columns: auto auto;
    grid-template-rows: auto auto;
  }

  .chosen-products {
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 1;
    grid-row-end: 2;
    // border: 1px solid springgreen;
    border-bottom: 1px solid gainsboro;
    width: 115.3rem;
    height: auto;
    @include flex-centered-totally;
  }
}

@media (max-width: 1200px) {
  .sidebar {
    width: 14rem; //auto;
    grid-gap: 2rem;
  }

  .chosen-products {
    width: 92.3rem;
  }
}

@media (max-width: 1000px) {
  .sidebar {
    width: 76rem;
    height: auto;
    grid-template-columns: auto auto auto;
    grid-auto-rows: auto;
    grid-gap: 1rem;
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 2;
    grid-row-end: 3;
    // border: 1px solid blue;
  }

  .chosen-products {
    width: 76rem;
  }
}

@media (max-width: 850px) {
  .sidebar,
  .feed,
  .chosen-products {
    width: 32rem;
  }

  .sidebar {
    grid-template-columns: auto auto;
    grid-auto-rows: auto;
  }
}
</style>