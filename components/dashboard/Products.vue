<script setup lang="ts">
import { ref } from 'vue';

const products = ref<Product[]>([])

try {
    products.value = await getAllProducts()
    console.log(products.value)
} catch (error) {
    console.error("error:", error);
    // (document.getElementById("error-message") as HTMLParagraphElement).innerText = "error:" + error.message;
}
</script>

<template>
 <div class="product-grid">
   <div v-for="product in products" :key="product.Id" class="product-icon">
     <i class="fas fa-cube"></i>
     <Nuxt-link :to="`/product/${product.Name}`">
       <p>{{ product.Name }}</p>
     </Nuxt-link>
   </div>
 </div>
</template>


<style scoped>
.product-grid {
 display: grid;
 grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
 grid-auto-rows: auto;
 gap: 20px;
 padding: 20px;
 width: 50%;
}

.product-icon {
 display: flex;
 flex-direction: column;
 align-items: center;
 justify-content: center;
 background-color: var(--bg);
 padding: 20px;
 border-radius: 10px;
 box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
 transition: transform 0.3s ease-in-out;
}

.product-icon:hover {
 transform: scale(1.05);
}

.product-icon i {
 font-size: 50px;
 color: var(--primary-accent-1);
}

.product-icon p {
 margin-top: 10px;
 font-size: 20px;
 color: var(--text);
}
</style>
