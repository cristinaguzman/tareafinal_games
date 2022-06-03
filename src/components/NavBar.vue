<template>
  <div class="bg-dark bg-info">
    <nav class="container navbar navbar-expand-lg navbar-dark bg-info">
      <a class="navbar-brand" href="#">Games Opinion</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active pr-4">
            <router-link class="nav-link" to="/">
              HOME
              <i class="fa fa-home" aria-hidden="true"></i>
            </router-link>
          </li>
          <li class="nav-item active pl-2">
            <router-link class="nav-link" to="/opinions">
              OPINIONES <i class="fa fa-commenting-o" aria-hidden="true"></i>
            </router-link>
          </li>
          <li class="nav-item active pl-2">
            <router-link class="nav-link" to="/management">
              ADMINISTRACION <i class="fa fa-cog" aria-hidden="true"></i>
            </router-link>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
