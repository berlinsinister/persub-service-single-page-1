<template>
  <div class="single-service-container">
    <div class="single-service-image">
      <img
        :src="require('../assets/images/' + url)"
        alt="single service content"
      />
      <div v-html="heart" class="heart"></div>
      <div class="linear-gradient-black"></div>
      <div class="info">
        <div class="title-and-description">
          <div>
            <div class="title">{{ title }}</div>
            <div class="description">{{ description }}</div>
          </div>
          <div class="subscribers">
            გამოწერილი აქვს {{ subscribers }} ადამიანს
          </div>
        </div>
        <div class="stars-and-comments">
          <div v-html="stars" class="stars"></div>
          <div class="comments">{{ comments }} კომენტარი</div>
        </div>
      </div>
    </div>
    <div class="options">
      <span class="choose">შეარჩიე პროდუქტები</span>
      <div v-for="(detail, index) in optionsDetails" :key="index">
        <Options
          :title="detail.title"
          :border="detail.border"
          :price="detail.price"
        />
      </div>
    </div>
    <div class="service-provider">
      <span class="choose">სერვისის მომწოდებელი</span>
      <ServiseProvider />
    </div>
  </div>
</template>

<script>
import Options from "./Options.vue";
import ServiseProvider from "./ServiceProvider.vue";

export default {
  name: "Single Service",
  components: { Options, ServiseProvider },
  props: {
    title: String,
    description: String,
    url: String,
    subscribers: Number,
    comments: Number,
  },
  data() {
    return {
      heart: `&#x2764;`,
      stars: `
        <i class="fa fa-star"></i>
        <i class="fa fa-star"></i>
        <i class="fa fa-star"></i>
        <i class="fa fa-star"></i>
        <i class="fa fa-star-o"></i>`,
      optionsDetails: [
        {
          title: "ჟუჟუნა კენკრის",
          border: "1px solid #7f6868",
          price: 15,
        },
        {
          title: "ჟუჟუნა ჟოლოს",
          border: "1px solid #c66f6c",
          price: 17,
        },
        {
          title: "ჟუჟუნა ბანანის",
          border: "1px solid #d4d278",
          price: 21,
        },
        {
          title: "ჟუჟუნა კენკრის",
          border: "1px solid #7f6868",
          price: 15,
        },
        {
          title: "ჟუჟუნა ჟოლოს",
          border: "1px solid #c66f6c",
          price: 17,
        },
        {
          title: "ჟუჟუნა ბანანის",
          border: "1px solid #d4d278",
          price: 21,
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.single-service-container {
  width: 76rem;
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  // border: 1px solid red;
  box-shadow: -11px 0px 8px -10px rgba(gray, 0.2),
    0px 11px 8px -10px rgba(gray, 0.2), 11px 0px 8px -10px rgba(gray, 0.2);
  & .single-service-image,
  & .options,
  & .service-provider {
    width: inherit;
    position: relative;
  }
  .single-service-image {
    & img {
      width: inherit;
      height: 42.5rem;
      object-fit: cover;
      border-top-left-radius: 1.5rem;
      border-top-right-radius: 1.5rem;
      transition: $transition-time ease-out;
      &:hover {
        filter: brightness(1.1);
      }
    }
    & .heart {
      position: absolute;
      top: 2rem;
      right: 3rem;
      font-size: 4rem;
      background: -webkit-linear-gradient(0deg, #ea7a9f, #eb8ea5);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      transition: $transition-time ease-out;
      &:hover {
        cursor: pointer;
        transform: scale(1.1);
        filter: brightness(1.2);
      }
    }
    & .linear-gradient-black {
      width: inherit; // 76rem;
      height: 10rem;
      position: absolute;
      bottom: 0.3rem; // for better overlay
      left: 0;
      background: linear-gradient(0deg, rgba(black, 0.5), rgba(black, 0));
    }
    & .info {
      position: absolute;
      bottom: 3rem;
      left: 3.5rem;
      // border: 1px solid crimson;
      width: 70rem;
      display: grid;
      grid-template-columns: auto;
      grid-auto-rows: auto;
      color: white;
      font-family: "DejaVu Sans Condensed", sans-serif;
      & .title-and-description,
      & .stars-and-comments {
        // border: 1px solid blue;
        display: grid;
        grid-template-columns: auto auto;
        grid-template-rows: auto;
        padding: 1rem 0;
      }
      & .title-and-description {
        border-bottom: 1px solid white;
        // padding-bottom: 2rem;
        & .title {
          font-size: 5rem;
          font-weight: 500;
        }
        & .description {
          font-size: 1.4rem;
        }
        & .subscribers {
          font-size: 1.4rem;
          align-self: end;
          justify-self: end;
        }
      }
      & .stars-and-comments {
        // border: 1px solid lime;
        & .stars {
          opacity: 0.5;
        }
        & .comments {
          align-self: end;
          justify-self: end;
        }
      }
    }
  }
  & .options {
    height: auto; // 20rem;
    display: grid;
    grid-template-columns: auto;
    grid-template-rows: repeat(6, auto);
    grid-gap: 1.5rem;
    justify-content: center;
    padding: 2.5rem 0;
    background: white;
    border-bottom: 1px dashed gainsboro;
  }
  & .service-provider {
    // border: 1px solid lime;
    display: grid;
    grid-template-columns: auto;
    grid-template-rows: auto auto;
    justify-content: center;
    padding: 2.5rem 0;
    background: white;
    color: #2f5371;
    border-bottom-left-radius: 1.5rem;
    border-bottom-right-radius: 1.5rem;
  }
}

.choose {
  color: #2f5371;
  font-family: "DejaVu Sans Condensed", sans-serif;
  font-size: 2rem;
}

// MEDIA
@media (max-width: 850px) {
  $smallest-media-width: 32rem;
  .single-service-container {
    width: $smallest-media-width; // 76rem;
    // border: 1px solid red;
    & .single-service-image {
      & img {
        width: inherit;
        height: 18rem; // 42.5rem;
      }
      & .heart {
        top: 1rem;
        right: 1.5rem;
        font-size: 2.5rem;
      }
      & .linear-gradient-black {
        width: inherit;
        height: 5rem;
      }
      & .info {
        bottom: 1rem;
        left: 1rem;
        // border: 1px solid crimson;
        width: $smallest-media-width - 2rem;
        & .title-and-description {
          grid-template-columns: auto;
          grid-template-rows: auto auto;
          padding: 0.5rem 0;
          & .title {
            font-size: 3rem;
          }
          & .subscribers {
            align-self: start; // end;
            justify-self: start; // end;
          }
        }
        & .stars-and-comments {
          padding: 0.5rem 0;
        }
      }
    }
    & .options {
      grid-gap: 1.5rem;
      padding: 1.5rem 0;
      // border: 1px solid green;
    }
    & .service-provider {
      padding: 1.5rem 0;
    }
  }

  .choose {
    font-size: 1.6rem;
  }
}
</style>