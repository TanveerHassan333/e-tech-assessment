<template> 
    <div>
        <h1 class="fw-semibold">Products List</h1>
        <p v-if="pending">Loading ....</p>
        <p v-else-if="error">Failed to load products</p>
        <div v-else>
            <div class="grid grid-cols-1 gap-6 sm-grid-cols-2 lg-grid-cols-3 xl-grid-cols-4" >
                <article v-for="product in data.products" :key="product.id" class="group overflow-hidden rounded-2xl border border-gray-200 bg-white shadow-sm transition-duration-300 hover:-translate-y-1 hover:shadow-xl">
                    <div class="relative aspect-square overflow-hidden bg-gray-100">
                        <img :src="product.thiumbnail" :alt="product.title" class="h-full w-full object-cover transition -duration-500 group-hover:scale-105" loading="lazy">
                        <span class="absolute left-3 top-3  rounded-full bg-white/90 px-3 py-1 text-xs font-medium capitalize text-gray-700 shadow-sm backdrop-blur">
                            {{ product?.category }}
                        </span>
                    </div>
                    <!-- content -->
                     <div class="p-5">
                        <h2 class="line-clamp-1 text-lg font-semibold text-gray-900" :title="product?.title">{{ product?.title }}</h2>
                        <p class="mt-2 line-clamp-2 min-h-[40px] text-sm leading-5 text-gray-500">{{ product?.description }}</p>
                     </div>
                </article>
                <!-- <img src="product?.thumbnail" alt="product image"> -->
                <!-- <h2>{{ product?.title }}</h2>
                 <p>{{ product?.description }}</p>
                <p>{{ product.price }}</p> -->
                
                 <!-- {{ product }} -->
            </div>
        </div>
    </div>
</template>
<script setup>
const { data , pending, error } = await useFetch('https://dummyjson.com/products?limit=20');
</script>