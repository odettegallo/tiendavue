<template>
  <div>
    <header class="hero bg-primary text-white text-center py-5">
      <div class="container">
        <h1 class="hero__title">Explora nuestra tienda de tecnología</h1>
        <p class="hero__subtitle">
          Descubre gadgets y accesorios con la mejor calidad y precio.
        </p>
      </div>
    </header>
    <div>
      <div class="modal fade" id="productDetailModal" tabindex="-1" aria-labelledby="productDetailModalLabel"
        aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
          <div class="modal-content" v-if="state.selectedProduct">
            <div class="modal-header">
              <h5 class="modal-title" id="productDetailModalLabel">
                {{ state.selectedProduct.name }}
              </h5>
              <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Cerrar"></button>
            </div>
            <div class="modal-body">
              <img :src="state.selectedProduct.image" class="img-fluid mb-3" :alt="state.selectedProduct.name" />
              <p><strong>Precio:</strong> ${{ state.selectedProduct.price.toLocaleString('es-CL') }}</p>
              <p><strong>Stock disponible:</strong> {{ state.selectedProduct.stock }}</p>
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">
                Cerrar
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>


    <main class="container pb-5">
      <section v-if="state.view === 'home'">
        <h5 class="h4 mb-3">Productos</h5>
        <SearchBox v-model="state.search" placeholder="Buscar por nombre..." class="mb-3" />
        <ProductList />
      </section>

      <section v-else-if="state.view === 'cart'">
        <h1 class="h4 mb-3">Carrito</h1>
        <CartTable />
      </section>

    </main>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { state, actions } from '../state'
import SearchBox from '../components/SearchBox.vue'
import ProductList from '../components/ProductList.vue'
import CartTable from '../components/CartDetail.vue'
import LoginForm from './Login.vue'

const cartCount = computed(() => state.items.reduce((a, it) => a + it.qty, 0))
const go = actions.go
const logout = actions.logout
</script>
