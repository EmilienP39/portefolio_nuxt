<template>
  <div id="skills">
    <div class="container">
      <div class="skill-box">
        <carousel :items-to-show="this.nb_itmes" snapAlign="center" class="carousel">
          <slide v-for="(item, index) in items" :key="index" class="carousel-item">
            <div class="circular-progress" :class="'circular-' + item.pourcentage">
              <div class="progress-value" v-if="item.nom !=='Anglais'">
                {{ item.pourcentage }}%
              </div>
              <div class="progress-value" v-else>
                C1
              </div>
            </div>
            <p >{{ item.nom }}</p>
          </slide>

          <template #addons>
            <navigation>
              <template #next>
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path d="M10 20A10 10 0 1 0 0 10a10 10 0 0 0 10 10zM8.711 4.3l5.7 5.766L8.7 15.711l-1.4-1.422 4.289-4.242-4.3-4.347z"/></svg>
              </template>
              <template #prev>
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path d="M10 20A10 10 0 1 0 0 10a10 10 0 0 0 10 10zM8.711 4.3l5.7 5.766L8.7 15.711l-1.4-1.422 4.289-4.242-4.3-4.347z"/></svg>
              </template>
            </navigation>
          </template>
        </carousel>
      </div>
    </div>
    <img class="background-image-left" src="assets/color-sharp.png" alt="Image" />
  </div>
</template>

<script lang="ts">
import 'vue3-carousel/dist/carousel.css'
import {Carousel, Slide, Navigation} from 'vue3-carousel'
import { ref } from 'vue'


export default defineComponent({
  components: {
    Carousel,
    Slide,
    Navigation
  },
  data() {
    return {
      items: [
        {
          pourcentage: "70" as string,
          nom: "VueJS (typescript)" as string
        },
        {
          pourcentage: "80" as string,
          nom: "Symfony" as string
        },
        {
          pourcentage: "70" as string,
          nom: "Anglais" as string
        },
        {
          pourcentage: "60" as string,
          nom: "Laravel" as string
        },
        {
          pourcentage: "60" as string,
          nom: "SQL" as string
        }
      ],
      nb_itmes: 3 as number
    }
  },
  mounted() {
    if(ref(screen.width).value <= 500){
      this.nb_itmes = 1;
    }
  }
})
</script>

<style>
.carousel-item {
  display: flex;
  padding: 0 20px;
  flex-direction: column;
  text-align: center;
  border-radius: 5px;
}

.skill-box {
  display: flex;
  width: 1000px;
  height: 300px;
  background: #090808;
  border-radius: 64px;
  text-align: center;
  justify-content: center;
  padding: 60px 50px;
  margin-top: -60px;
}

.container {
  margin: auto;
  display: flex;
  justify-content: center;
}

.circular-progress{
  position: relative;
  height: 160px;
  width: 160px;
  border-radius: 50%;
  animation: rotation 1s ease-in-out;
  display: flex;
  align-items: center;
  justify-content: center;
}
.circular-progress::before{
  content: "";
  position: absolute;
  height: 125px;
  width: 125px;
  border-radius: 50%;
  background-color: #151515;
}

.circular-50{
  background: conic-gradient(from 60deg,#5730B4 90deg,#9F3583 180deg , #151515 0deg);
}

.circular-60{
  background: conic-gradient(from 60deg,#5730B4 108deg,#9F3583 216deg , #151515 0deg);
}

.circular-70{
  background: conic-gradient(from 60deg,#5730B4 126deg,#9F3583 252deg , #151515 0deg);
}

.circular-80{
  background: conic-gradient(from 60deg,#5730B4 144deg,#9F3583 288deg , #151515 0deg);
}

.circular-90{
  background: conic-gradient(from 60deg,#5730B4 162deg,#9F3583 324deg , #151515 0deg);
}

.background-image-left {
  top: 60%;
  position: absolute;
  bottom: 0;
  width: 40%;
  z-index: -4;
}

.progress-value {
  animation: -rotation 1s ease-in-out;
  position: relative;
  font-size: 25px;
  font-weight: 600;
  color: #fff;
}

.carousel__prev svg {
  transform:rotate(-180deg);
  z-index: 5;
  background: white;
  border-radius: 50%;
}
.carousel__next svg {
  z-index: 5;
  background: white;
  border-radius: 50%;
}

</style>
