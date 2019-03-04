<template>
  <div class="dribbble-shots">
    <shot
      v-for="(shot, index) in shots"
      :key="index"
      :index="index"
      :shot="shot"></shot>
  </div>
</template>

<script>
import Shot from './components/Shot.vue';

export default {
  name: 'DribbbleShots',
  props: {
    user: {
      type: String,
      required: true,
    },
    token: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      shots: [],
    };
  },
  mounted() {
    if (window.axios) {
      window.axios.get('https://api.dribbble.com/v2/user/shots?per_page=5', {
        headers: {
          Authorization: `Bearer ${this.token}`
        },
      }).then(response => {
        this.shots = response.data;
      }).catch(err => { throw err });
    }
  },
  components: {
    Shot,
  },
};
</script>

<style scoped>
.dribbble-shots {
  display: grid;
  grid-gap: 15px;
  grid-template-areas: 
    "card-1 card-1 card-1 card-2"
    "card-1 card-1 card-1 card-3"
    "card-4 card-4 card-5 card-5";
}

@media (max-width: 768px) {
  .dribbble-shots {
    grid-template-areas: 
      "card-1 card-1 card-1 card-1"
      "card-1 card-1 card-1 card-1"
      "card-2 card-2 card-3 card-3"
      "card-4 card-4 card-5 card-5";
  }
}
</style>