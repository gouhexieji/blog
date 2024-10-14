<script setup lang="ts">
import axios from "axios";
import { onMounted, ref } from 'vue';

const isLoading = ref<boolean>(true);
const links = ref<Array<Link>>([]);

type Link = {
    name: string;
    site: string;
    siteURL: string;
    icon: string;
};

const loadData = () => {
    // Here you can modify or leave the API call empty to clear the existing links
    links.value = [];  // Clear the links
    isLoading.value = false;  // Set loading to false immediately
};

onMounted(() => {
    loadData();
});
</script>

<template>
    <div>
        <div v-if="isLoading">
            <p class="text-center">Loading……</p>
        </div>
        <div v-else class="grid grid-cols-1 gap-3.5 md:grid-cols-2 mb-3">
            <p class="text-center">No links available.</p>  <!-- Message when links are cleared -->
        </div>
        <p class="text-xs text-right">📧:
            <a class="link" href="mailto:kasumi@bangdream.moe">
                kasumi@bangdream.moe
            </a>
        </p>
    </div>
</template>

<style scoped>
.card-hover {
  position: relative;
  transform: translateY(0);
  transition: all 0.3s ease;
}
.card-hover:hover {
  transform: translateY(-5px);
}
</style>

