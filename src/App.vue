<template>
  <Scrollama @step-enter="stepEnterHandler">
    <div slot="graphic" class="graphic">This is a graphic</div>
  </Scrollama>
</template>

<template>
  <div>
    <Scrollama @step-enter="stepEnterHandler">
      <div slot="graphic" class="graphic">
        <p>{{currStepId}}</p>
        <div :class="[{staticClass: true}, currStepId]">
          <img src="logo2.png" alt="Current" id="image">
          <img v-for="img in images" v-bind:src="img.path" :class="img.id" />
        </div>
      </div>
      <div class="step" :class="{'is-active': currStepId == 1}" data-step="a" data-step-id="1">Hi hello! My name is <a href="https://www.linkedin.com/in/juweek">Juweek Adolphe</a> and I live in Brooklyn, NY. I'm 26 years old, the youngest child of two Haitian immigrants, and an extremely curious person. I love learning about things.</div>
      <div class="step" :class="{'is-active': currStepId == 2}" data-step="b" data-step-id="2"><span>It's always a bit of a challenge describing what I do for a living: I code, I draw, I work with data, and so much more. There is great value in playing within the in-between areas of disciplines, and that's my dream: to use multiple disciplines to tell meaningful stories.</span> <span>There are many out there who aren't the best at learning through the traditional academic way. I want to make them feel seen</span></div>
      <div class="step" :class="{'is-active': currStepId == 3}" data-step="c" data-step-id="3"><span>Most recently and importantly, I was a journalist at the Guardian for almost three years. I studied computer science, and used created code and design to create visual, interactive stories.</span> <span>I left that job and now work for a government contractor, but telling stories is where my heard relies, and I picked up a lot of skills from the newsroom.</span></div>
      <div class="step" :class="{'is-active': currStepId == 4}" data-step="d" data-step-id="4"><span>Feel free to expore some of my work: for my proposal, I want to emphasize my drawing abilities, my ability to animate, and my ability to code.</span> <span> <a href="https://www.theguardian.com/technology/ng-interactive/2019/feb/20/how-to-catch-a-catfisher">To Catch a Catfisher</a> | <a href="https://www.theguardian.com/us-news/ng-interactive/2019/apr/12/black-women-on-colorism-hollywood-entertainment-industry-panel">Shades of Black interviews</a> | Link to Instagram </span></div>
      <div class="step" :class="{'is-active': currStepId == 5}" data-step="c" data-step-id="5"><span>Tech is great, but illustration and visual content offer immediacy and accessible entry. Abstractly, in the future I want to communicate with images and websites. Concretely, I want to create a new type of educational content.</span> <span>This can range from starting my own thing, to joining existing missions like Brilliant, to becoming an old-fashioned teacher.</span></div>
  </Scrollama>
</div>
</template>

<script>
import 'intersection-observer' // for cross-browser support
import Scrollama from 'vue-scrollama'

export default {
  components: {
    Scrollama
  },
  data() {
    return {
      currStepId: null,
      steps: [
        {id: '1'},
        {id: '2'},
        {id: '3'},
        {id: '4'}
      ],
      images:[
        {id: '1', path: "https://media.illustrationx.com/images/artist/ButcherBilly/109328/crop/500/stan-lee-illustration.jpg"},
        {id: '2', path: "https://i.pinimg.com/236x/7f/c6/29/7fc629c601b5350bdfbc7f39e27294dc--martin-wittfooth-goth-art.jpg"}
      ]
    }
  },
  methods: {
    stepEnterHandler({element, direction, index}) {
      console.log({element, direction, index});
      this.currStepId = element.dataset.stepId
    }
  }
}
</script>

<style src="vue-scrollama/dist/vue-scrollama.css"></style>
<style>@import url('https://fonts.googleapis.com/css2?family=Proza+Libre&display=swap');</style>
<style scoped>

.step {
  width: 80%;
  max-width: 40rem;
  padding: 6rem 20px;
  margin: 0 auto 40rem;
  border: 1px solid #767676;
  background: rgba(241, 240, 236, .6);
  justify-content: center;
  font-size: 21px;
  line-height: 28px;
  box-shadow: 3px 3px 3px #999;
  font-family: "Proza Libre", Helvetica, Arial;
}
.step span {
  display: block;
  padding-bottom: 20px;
}
.step.is-active {
  background-color: beige;
}
.graphic {
  height: 60vh;
  width: 40vw;
  background-color: #F1F0EC;
  display: flex;
  margin: 0 auto;
  align-items: center;
  justify-content: center;
  font-size: 5rem;
}
</style>
