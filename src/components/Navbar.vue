<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container">
      <a class="navbar-brand" href="#" @click.prevent="go('home')">TechGadget Store</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#nav">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div id="nav" class="collapse navbar-collapse">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="#" @click.prevent="go('home')">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" @click.prevent="go('cart')">Carrito ({{ cartCount }})</a>
          </li>
        </ul>
        <div class="d-flex align-items-center gap-2">
          <span v-if="state.user">Hola, {{ state.user.name || state.user.email }}</span>
          <a v-if="!state.user" class="btn btn-outline-primary btn-sm" href="#" @click.prevent="go('login')">Iniciar sesión</a>
          <button v-else class="btn btn-outline-secondary btn-sm" @click="logout">Cerrar sesión</button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { computed } from 'vue'
import { state, actions } from '../state'

// Calcula el total de ítems en el carrito.
const cartCount = computed(() => state.items.reduce((a, it) => a + it.qty, 0))
const go = actions.go
const logout = actions.logout
</script>
