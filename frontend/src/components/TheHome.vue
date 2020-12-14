<template>
  <div>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <form class="d-flex">
          <button
            class="btn btn-outline-success"
            @click.prevent="logout"
            type="button"
          >
            Logout
          </button>
        </form>
      </div>
    </nav>
    <div class="container">
      <div class="alert alert-primary" role="alert">
        {{ user.nombre }}
      </div>
      <div class="alert alert-secondary" role="alert">
        {{ user.email }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {},
    };
  },
  methods: {
    getUserDetails() {
      let user = localStorage.getItem("user");
      //let token = localStorage.getItem("jwt");

      this.user = JSON.parse(user);
    },
    logout() {
      localStorage.removeItem("jwt");
      localStorage.removeItem("user");
      this.$router.push("/");
    },
  },
  created() {
    this.getUserDetails();
  },
};
</script>

<style></style>
