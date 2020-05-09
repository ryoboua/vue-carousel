<template>
  <div>
    <div class="carousel-container">
      <div ref="carouselSlider" class="carousel-slider">
        <Card
          ref="card"
          v-for="(d, i) in cardsData.slice(
            cardsData.length - numOfCardsDisplayed,
            numOfCardsDisplayed.length
          )"
          :key="`backClone${i}`"
          :data="d"
          id="backClone"
          class="card-carousel"
        />
        <Card
          ref="card"
          v-for="(d, i) in cardsData"
          :key="i"
          :data="d"
          class="card-carousel"
        />
        <Card
          ref="card"
          v-for="(d, i) in cardsData.slice(0, numOfCardsDisplayed)"
          :key="`frontClone${i}`"
          :data="d"
          id="frontClone"
          class="card-carousel"
        />
      </div>
    </div>
    <div id="prevBtn" @click="handlePrevious"></div>
    <div id="nextBtn" @click="handleNext"></div>
  </div>
</template>

<script>
import Card from "./Card.vue"
import cardsData from "../data"
export default {
  components: {
    Card,
  },
  mounted() {
    this.position = this.initialPosition
    this.$refs.carouselSlider.style.transform = `translateX(${-this.position *
      (this.cardWidth + 50)}px)`

    this.$refs.carouselSlider.addEventListener("transitionend", () => {
      if (
        this.$refs.card[this.position].$el.id === "frontClone" &&
        this.$refs.card[this.position + 1].$el.id === "frontClone" &&
        this.$refs.card[this.position + 2].$el.id === "frontClone"
      ) {
        this.$refs.carouselSlider.style.transition = "none"
        this.position = this.initialPosition
        this.$refs.carouselSlider.style.transform = `translateX(${-this
          .position *
          (this.cardWidth + 50)}px)`
      }

      if (
        this.$refs.card[this.position].$el.id === "backClone" &&
        this.$refs.card[this.position + 1].$el.id === "backClone" &&
        this.$refs.card[this.position + 2].$el.id === "backClone"
      ) {
        this.$refs.carouselSlider.style.transition = "none"
        this.position = this.cardsData.length
        this.$refs.carouselSlider.style.transform = `translateX(${-this
          .position *
          (this.cardWidth + 50)}px)`
      }
    })
  },
  computed: {
    cardWidth: function() {
      return this.$refs.card[0].$el.getBoundingClientRect().width
    },
  },
  data() {
    return {
      initialPosition: 3,
      numOfCardsDisplayed: 3,
      position: null,
      cardsData,
    }
  },
  methods: {
    handleNext() {
      if (this.position >= this.$refs.card.length - 3) return
      this.$refs.carouselSlider.style.transition = "transform 0.4s ease-in-out"
      this.position++
      this.$refs.carouselSlider.style.transform = `translateX(${-this.position *
        (this.cardWidth + 50)}px)`
    },
    handlePrevious() {
      if (this.position <= 0) return
      this.$refs.carouselSlider.style.transition = "transform 0.4s ease-in-out"
      this.position--
      this.$refs.carouselSlider.style.transform = `translateX(${-this.position *
        (this.cardWidth + 50)}px)`
    },
  },
}
</script>

<style>
.carousel-container {
  position: relative;
  width: 80%;
  margin: 40px auto;
  overflow: hidden;
}

.carousel-slider {
  display: flex;
  widows: 100%;
  margin-bottom: 1px;
}

.card-carousel {
  margin-right: 50px;
}

#prevBtn {
  position: absolute;
  top: 50%;
  left: 5%;
  z-index: 10;
  font-size: 30px;
  cursor: pointer;
  width: 27px;
  height: 42px;
  margin-top: -15px;
  margin-left: 50px;
}

#prevBtn::before {
  position: absolute;
  content: "";
  width: 100%;
  height: 5px;
  background-color: #747069;
  transform-origin: left;
  transform: rotate(45deg);
  opacity: 0.5;
  border-radius: 5px;
  top: 45%;
}
#prevBtn::after {
  position: absolute;
  content: "";
  width: 100%;
  height: 5px;
  background-color: #747069;
  transform-origin: left;
  transform: rotate(-45deg);
  opacity: 0.5;
  border-radius: 5px;
  top: 48%;
}
#nextBtn {
  position: absolute;
  top: 50%;
  right: 5%;
  z-index: 10;
  font-size: 30px;
  cursor: pointer;
  width: 27px;
  height: 42px;
  margin-top: -15px;
  margin-right: 50px;
}

#nextBtn::before {
  position: absolute;
  content: "";
  width: 100%;
  height: 5px;
  background-color: #747069;
  transform-origin: right;
  transform: rotate(45deg);
  opacity: 0.5;
  border-radius: 5px;
  top: 48%;
}
#nextBtn::after {
  position: absolute;
  content: "";
  width: 100%;
  height: 5px;
  background-color: #747069;
  transform-origin: right;
  transform: rotate(-45deg);
  opacity: 0.5;
  border-radius: 5px;
  top: 45%;
}
</style>
