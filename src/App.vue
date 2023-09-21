<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container">
        <RouterLink to="/" class="navbar-brand">
          <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="70" height="70" />
        </RouterLink>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <RouterLink to="/" class="nav-link">Home</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink to="/products" class="nav-link">Shop</RouterLink>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>

  <section class="wrapper">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <main>
            <RouterView />
          </main>
        </div>
      </div>
    </div>
  </section>
</template>
