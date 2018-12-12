<template>
<main>
    <Nav />
    <h1>{{ $route.params.kmom }}</h1>
    <div class="question" v-for="question in questions" :key="question.key">
      <p><strong>{{ question.question }}</strong></p>
      <p>{{ question.answer }}</p>
    </div>
</main>

</template>

<script>
import Nav from './Nav.vue'

export default {
  name: 'Report',
  components: {
    Nav,
  },
  data() {
    return {
      questions: [],
    }
  },
  mounted() {
    this.getText(this.$route.params.kmom);
  },
  methods: {
    getText(kmom) {
      let that = this;
      that.text = "";
      fetch("https://me-api.emilfolino.se/reports/" + kmom)
      .then(function(response) {
          return response.json();
      })
      .then(function(result) {
          // eslint-disable-next-line
          console.log(result);
          that.questions = result.data.map((question, index) => {
            return {
              key: index,
              question: question.question,
              answer: question.answer
            };
          });
      });
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  text-transform: uppercase;
}

.question {
  margin-bottom: 2em;
}
</style>
