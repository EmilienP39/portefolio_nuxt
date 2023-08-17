<template>
  <section class="banner" id="home">
    <div class="container">
      <div class="content">
        <span class="tagline">Welcome to my Portfolio</span>
        <h1>Bienvenue, moi c'est Emilien ! <br><span class="txt-rotate"><span class="wrap">{{ this.text }}</span></span>
        </h1>
        <p>Je m'appelle Emilien PAUL, j'ai 20 ans. Je suis actuellement en licence <a
            href="http://pasteurmontroland.com/formation/27/description?page=5" target="_blank"
            rel="noopener noreferrer">CAISI</a> au Lycée Pasteur Mont-Roland à Dole. A côté de ça, je suis alternant au
          collège Notre Dame de Mont-Roland toujours à Dole. En développement, j'utilise majoriterment <b>VueJS</b> avec
          <b>Typescript</b> en technologie front-end et <b>Symfony</b> pour le back-end.
        </p>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
export default defineComponent({
  data() {
    return {
      intervalId: 0 as number,
      toRotate: [ "Développeur Web", "Développeur Full Stack"] as String[],
      period: 2000 as number,
      delta: 200 - Math.random() * 100 as number,
      loopNum: 0 as number,
      isDeleting: false as boolean,
      text: "" as string,
      index: 0 as number,
    };
  },
  mounted() {
    setInterval(this.maAction, this.delta); // Appeler maAction toutes les 5 secondes (5000 ms)
  },
  methods: {
    maAction() {
      let i = this.loopNum % this.toRotate.length;
      let fullText = this.toRotate[i];
      let updatedText = this.isDeleting ? fullText.substring(0, this.text.length - 1) : fullText.substring(0, this.text.length + 1);

      this.text = updatedText;

      if (this.isDeleting) {
        let prevDelta:number = this.delta
        this.delta = prevDelta / 2;
      }

      if (!this.isDeleting && updatedText === fullText) {
        this.isDeleting = true;
        let prevIndex:number = this.index;
        this.index = prevIndex - 1;
        this.delta = this.period;
      } else if (this.isDeleting && updatedText === '') {
        this.isDeleting = false;
        this.loopNum++;
        this.index = 1;
        this.delta = 100;
      } else {
        let prevIndex:number = this.index;
        this.index = prevIndex + 1;
      }
    }
  }
});
</script>

<style>
.container{
  display: flex;
  align-items: center;
  flex-direction: row;
  flex-wrap: wrap;
}

.content{
  margin-right:28em;
  margin-left:28em;
}

.banner {
  margin-top: 0;
  padding: 260px 0 100px 0;
  background-image: url('assets/banner-bg.png');
  background-position: top center;
  background-size: cover;
  background-repeat: no-repeat;
}

.banner .tagline {
  font-weight: 700;
  letter-spacing: 0.8px;
  padding: 8px 10px;
  background: linear-gradient(90.21deg, rgba(170, 54, 124, 0.5) -5.91%, rgba(74, 47, 189, 0.5) 111.58%);
  border: 1px solid rgba(255, 255, 255, 0.5);
  font-size: 20px;
  margin-bottom: 16px;
  display: inline-block;
}

.banner h1 {
  font-size: 65px;
  font-weight: 700;
  letter-spacing: 0.8px;
  line-height: 1;
  margin-bottom: 20px;
  display: block;
}

.banner p {
  color: #B8B8B8;
  font-size: 18px;
  letter-spacing: 0.8px;
  line-height: 1.5em;
  width: 96%;
}

.banner button {
  color: #fff;
  font-weight: 700;
  font-size: 20px;
  margin-top: 60px;
  letter-spacing: 0.8px;
  display: flex;
  align-items: center;
}

.banner button svg {
  font-size: 25px;
  margin-left: 10px;
  transition: 0.3s ease-in-out;
  line-height: 1;
}

.banner button:hover svg {
  margin-left: 25px;
}

.banner img {
  animation: updown 3s linear infinite;
}

.txt-rotate > .wrap {
  border-right: 0.08em solid #666;
}
</style>