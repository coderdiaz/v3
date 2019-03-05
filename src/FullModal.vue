<template>
  <div :class="classes">
    <a href="#" @click.prevent="close" class="full-modal-icon">
      <svg id="Layer_1" version="1.1" viewBox="0 0 100 100" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><polygon fill="#fff" points="77.6,21.1 49.6,49.2 21.5,21.1 19.6,23 47.6,51.1 19.6,79.2 21.5,81.1 49.6,53 77.6,81.1 79.6,79.2   51.5,51.1 79.6,23 "/></svg>
    </a>
    <div class="full-modal-wrapper">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FullModal',
  props: {
    show: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    close() {
      this.$emit('close');
    },
  },
  computed: {
    active() {
      return this.show;
    },
    classes() {
      return {
        'full-modal': true,
        active: this.active,
      };
    },
  },
};
</script>

<style scoped>
.full-modal {
  background: rgba(0, 0, 0, 0.8);
  height: 100%;
  width: 100%;
  z-index: 9999;
  position: fixed;
  top: 0;
  left: 0;
  display: none;
}

.full-modal.active {
  display: block;
}
</style>
<style>
.menu__navigation {
  list-style: none;
  padding: 0;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  margin-right: -50%;
  position: absolute;
  text-align: center;
  color: #ffffff;
  font-size: 25px;
}

.menu__navigation .menu__navigation-link {
  color: #ffffff;
  text-decoration: none;
  font-weight: 700;
}

.separator {
  margin-bottom: 20px;
}

.menu__navigation .menu__navigation-link.menu--email {
  text-decoration: underline;
}

.full-modal-icon {
  position: absolute;
  right: 15px;
  top: 15px;
}

.full-modal-icon svg {
  width: 60px;
}
</style>

