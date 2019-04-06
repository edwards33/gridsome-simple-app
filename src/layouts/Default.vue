<template>
  <div class="bg">
    <header class="header">
      <strong>
        <g-link to="/">{{ $static.metaData.siteName }}</g-link>
      </strong>
      <nav class="nav">
        <g-link class="nav__link" to="/">Home</g-link>
        <g-link class="nav__link" to="/posts">Posts</g-link>
        <g-link class="nav__link" to="/about">About</g-link>
      </nav>
    </header>
    <g-image v-if="background" :src="background" class="billboard" />
    <div class="layout">
      <transition name="fade" appear>
        <main>
          <slot/>
        </main>
      </transition>

    </div>
    <div class="footer">
      <p class="footer-text"><span>&copy; 2019 Edward</span></p>
    </div>
  </div>
</template>

<static-query>
query {
  metaData {
    siteName
  }
}
</static-query>


<script>

  export default {
      props: ["background"],
  }
</script>

<style lang="scss">
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
  font-size: $baseFontSize;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
  padding-bottom: 10px;

  }

.bg {
  background-size: 150px;
  background-repeat: round;
  background-image: url("https://image.freepik.com/free-vector/vector-polka-background-with-small-dots_1017-13972.jpg");
}
.header {
  display: flex;
  max-width: 760px;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
  padding: 20px;
  margin: 0 auto;
}
.footer {
  clear: both;
  position: relative;
  height: 40px;
  margin-top: -40px;
  background-image: url("https://picsum.photos/1110/300/?random");
  color: white;
  text-align: center;
}
.footer-text {
  padding-top: 8px;
}

.footer-text span {
  padding: 5px;
  background-color: lightslategray;
  border-radius: 25px;
}

.billboard {
  width: 100%;
  height: auto;
}


.nav__link {
  margin-left: 20px;
}

.fade-enter-active {
  transition: 0.3s ease opacity;
}

.fade-enter {
  opacity: 0;
}
</style>
