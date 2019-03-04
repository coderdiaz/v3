<template>
  <div
    :class="classes"
    :style="style"
    @mouseenter.prevent="toggle"
    @mouseleave.prevent="toggle">
      <div v-if="shot" :class="classesLink">
        <a class="link" :href="shot.html_url">Show in Dribbble</a>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Shot',
  props: {
    shot: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    cardType: {
      type: String,
      default: 'card-sm',
    },
  },
  data() {
    return {
      active: false,
    };
  },
  computed: {
    classes() {
      return {
        'card__image': true,
        ['card-lg']: (this.index === 0),
        [this.cardType]: (this.index === 1 || this.index === 2),
        ['card-md']: (this.index === 3 || this.index == 4),
        [`card-${this.index + 1}`]: true,
      };
    },
    classesLink() {
      return {
        overlay: true,
        active: this.active, 
      };
    },
    style() {
      return {
        'background-image': `url(${this.shot.images.hidpi})`,
      };
    },
  },
  methods: {
    toggle() {
      this.active = !this.active;
    },
  }
};
</script>

<style scoped>
.card__image {
  background-size: cover;
  background-position: center;
  box-shadow: 0px 0px 10px 0px #cca08e;
  overflow: hidden;
  position: relative;
}

.card__image.card-lg {
  min-height: 450px;
}

.card__image.card-md {
  min-height: 250px;
}

/* Registering cards */
.card-1 { grid-area: card-1; }
.card-2 { grid-area: card-2; }
.card-3 { grid-area: card-3; }
.card-4 { grid-area: card-4; }
.card-5 { grid-area: card-5; }

/* Overlay */
.overlay {
  background: rgba(0, 0, 0, 0.8);
  height: 100%;
  width: 100%;
  z-index: 9999;
  position: absolute;
  display: none;
}
.overlay.active {
  display: block;
}

/* Styles for link */
.link {
  color: #ffffff;
  left: 50%;
  top: 50%;
  position: absolute;
  margin-right: -50%;
  transform: translate(-50%, -50%);
  font-size: 15px;
  font-family: 'Titillium Web', 'Roboto', 'Helvetica Neue', sans-serif;
  font-weight: 700;
  text-decoration: none;
}

/* Medium devices to down */
@media (max-width: 768px) {
  .card__image.card-sm {
    min-height: 200px;
  }
}

/* Small devices to down */
@media(max-width: 576px) {
  .card__image.card__image.card-lg {
    min-height: 245px;
  }
  .card__image.card-md {
    min-height: 150px;
  }
  .card__image.card-sm {
    min-height: 120px;
  }
}
</style>

