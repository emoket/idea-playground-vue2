<template>
  <v-container
    fluid
    fill-height
    style="background: #e3e3e3"
    class="d-flex justify-center align-center"
  >
    <v-btn color="primary" @click="click_btn_init"> 초기화 </v-btn>

    <v-overlay v-show="overlay" opacity="0.9">
      <v-col cols="12" class="mb-4">
        <v-scroll-y-reverse-transition>
          <h1 v-show="overlay" class="text display-3 font-weight-regular">
            작업공간을 초기화 하고 있습니다...
          </h1>
        </v-scroll-y-reverse-transition>
      </v-col>
    </v-overlay>

    <v-snackbar bottom right color="success" v-model="snackbar" timeout="2000">
      초기화 되었습니다.
    </v-snackbar>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    overlay: false,
    disappear: undefined,
    snackbar: false,
  }),
  methods: {
    click_btn_init() {
      const isConfirmed = confirm('초기화 하시겠습니까?');

      if (isConfirmed) {
        this.overlay = true;

        // split text into letters
        const text = document.querySelector('.text');
        text.innerHTML = text.textContent.replace(/\S/g, '<span>$&</span>');

        // add active class on hovered <span> tag
        const letters = document.querySelectorAll('span');
        this.disappear = setInterval(() => {
          let random_index = Math.floor(Math.random() * letters.length);
          console.log(`random_index --> ${random_index}`);
          letters[random_index].classList.add('active');
        }, 1000);

        setTimeout(() => {
          this.overlay = false;
          this.snackbar = true;
          clearInterval(this.disappear);
        }, 5000);
      }
    },
  },
};
</script>

<style>
.text span {
  position: relative;
  display: inline-block;
  cursor: pointer;
  user-select: none;
}
.text span.active {
  animation: smoke 2s linear forwards;
}
@keyframes smoke {
  0% {
    opacity: 1;
    filter: blur(0);
    transform: translateX(0) translateY(0) rotate(0deg) scale(1);
  }
  50% {
    opacity: 1;
    pointer-events: none;
  }
  100% {
    opacity: 0;
    filter: blur(40px);
    transform: translateX(300px) translateY(-300px) rotate(720deg) scale(3);
  }
}
</style>
