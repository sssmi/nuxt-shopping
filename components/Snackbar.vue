<template>
  <div class="snackbar-container">
    <transition name="snackbar-toggle">
      <div 
        v-if="show" 
        class="snackbar">
        <div class="snackbar__text">
          <span v-html="message"></span>
        </div>
        <div class="snackbar__action">
          <button 
            class="snackbar__button" 
            @click="hideSnackbar">X</button>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import { mapState } from 'vuex';
export default {
  computed: {
    ...mapState({
      show: state => state.snackbar.show,
      message: state => state.snackbar.message
    })
  },
  methods: {
    hideSnackbar() {
      this.$store.commit('hideSnackbar');
    }
  }
  // ,updated: function() {
  //   if (this.show) {
  //     console.log('updated!!!!!');
  //   } else console.log('going back!');
  // }
};
</script>

<style scoped lang="scss">
.snackbar-container {
  font-family: 'Montserrat', sans-serif;
  font-size: 12px;
  text-transform: uppercase;
  position: absolute;
  bottom: 0;
  left: 50%;
  display: flex;
}

.snackbar-button {
  font-family: 'Montserrat', sans-serif;
}
.snackbar {
  border-radius: 5px 5px 0 0;
  position: relative;
  left: -50%;
  display: flex;
  color: white;
  background: black;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
  min-width: 200px;
}

// Transition
.snackbar-toggle-enter-active,
.snackbar-toggle-leave-active {
  transition: all 0.4s ease;
}
.snackbar-toggle-enter,
.snackbar-toggle-leave-to {
  opacity: 0;
  transform: translateY(60px);
}
</style>
