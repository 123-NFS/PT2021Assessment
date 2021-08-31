<template>
  <div class="home">
    <div class="container bg-light">
      <img
        src="../assets/mkcl_logo.jpg"
        class="img-fluid"
        style="height: 200px; width: 200px"
        alt=""
      />
      <hr />

      <router-link :to="{ name: 'Register' }">
        <input
          type="submit"
          name="Register"
          id="mkcl_button"
          class="btn btn-outline-primary"
          value="Register"
        />
      </router-link>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "Home",
  components: {
    // HelloWorld
  },
};
</script>
