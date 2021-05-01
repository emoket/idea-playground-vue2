<template>
  <div id="container" ref="container" @mousemove="mouseMove">
    <div class="content">
      <h2>404</h2>
      <h4>Oops! Page not found</h4>
      <p>
        The page you were looking for doesn't exist. You may have mistyped the
        address or the page may have moved.
      </p>
      <a href="/">Back To Home</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NotFound',
  data: () => ({
    //
  }),
  methods: {
    mouseMove(e) {
      this.$refs.container.style.backgroundPositionX = `-${e.pageX / 5}px`;
      this.$refs.container.style.backgroundPositionY = `-${e.pageY / 5}px`;
    },
  },
};
</script>

<style scoped>
@import url(https://fonts.googleapis.com/css?family=Poppins:100,100italic,200,200italic,300,300italic,regular,italic,500,500italic,600,600italic,700,700italic,800,800italic,900,900italic);
* {
  font-family: 'Poppins', sans-serif;
}
#container {
  background: url('../assets/p404.png'), #151729;
  position: absolute;
  /* left: 10%;
  top: 10%;
  right: 10%;
  bottom: 10%; */
  width: 100%;
  height: 100vh;
  /* border-radius: 10px; */
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.5);
}
#container .content {
  max-width: 600px;
  text-align: center;
}
#container .content h2 {
  font-size: 14vw;
  color: #fff;
  line-height: 1em;
}
#container .content h4 {
  position: relative;
  font-size: 1.5em;
  margin-top: 20px;
  color: #111;
  background: #fff;
  font-weight: 300;
  padding: 10px 20px;
  margin-bottom: 25px;
  display: inline-block;
}
#container .content p {
  color: #fff;
  font-size: 1.2em;
}

#container .content a {
  position: relative;
  display: inline-block;
  padding: 10px 25px;
  background: #ff0562;
  color: #fff;
  text-decoration: none;
  margin-top: 25px;
  border-radius: 25px;
  border-bottom: 4px solid #d00d56;
}
</style>
