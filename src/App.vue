<template>
  <div>
    <Navbar />
    <div style="height: 56px;"></div> <!-- Espacio para la barra de navegación fija -->
    <section v-if="state.view === 'home'">
      <Home />
    </section>

    <section v-else-if="state.view === 'cart'">
      <CartDetail />
    </section>

    <section v-else-if="state.view === 'login'">
      <Login />
    </section>
  </div>
</template>

<script setup>
import { state } from './state'
import Navbar from './components/Navbar.vue'
import CartDetail from './components/CartDetail.vue'
import Home from './views/Home.vue'
import Login from './views/Login.vue'

</script>
