<template>
  <div class="service-card">
    <div class="service-card-header">
    <img
      :src="provider.imageUrl"
      alt="Profile"
      class="service-provider-image"
    >
    <div class="provider-info">
      <h3 class="provider-name">
        {{ provider.name }}
      </h3>
      <div class="provider-rating">
        {{ provider.rating }}
        <span v-for="star in roundedStars" :key="star" class="filled-star">★</span>
        <span v-for="star in 5 - roundedStars" :key="star" class="empty-star">☆</span>
        ({{ provider.reviewsCount }} reviews)
    </div>
    </div>
    <div class="status-badge">
      <p>
        {{ provider.isAnAdd ? 'Mainos' : 'Kanta ✔️' }}
      </p>
    </div>
  </div>
    <div class="service-card-body">
      <div class="service-card-logo">
        <img :src="provider.logoUrl" alt="Medistep Logo" class="logo-img" />
      </div>
      <div class="service-details">
        <div class="provider-service-name">
          {{ provider.ServiceName }}
        </div>
        <div class="provider-address">
          {{ provider.address }}
        </div>
      </div>
    </div>
    <div class="service-card-footer" v-if="provider.availableTimes && provider.availableTimes.length > 0">
    <p class="service-card-next-time">Seuraava aika</p>
    <div class="available-times">
      <span class="time-slot" v-for="time in provider.availableTimes" :key="time">
        {{ time }}
      </span>
    </div>
  </div>
  </div>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const props = defineProps({
  provider: {
    type: Object,
    required: true
  }
})



const roundedStars = computed(() => Math.round(props.provider.rating));
</script>

<style lang="scss" scoped>
.service-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  margin-bottom: 1rem;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  background-color: #fff;
  height: max-content;
  width: 400px; 
}

.service-card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  margin-top: 0.5rem;
}
.filled-star {
  color: black; 
}

.empty-star {
  color: #ccc;
}

.status-badge {
  padding: 0.25rem 0.75rem;
  border-radius: 10px; 
  font-size: 0.75rem; 
  display: flex;
  align-items: center;
  justify-content: center;
  height: fit-content;
  position: relative;
  top: -30px;
  right: -10px;
}
.service-provider-image {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  object-fit: cover;
  margin-right: 1rem;
}

.provider-info {
  flex-grow: 1;
  padding-left: 1rem;
}

.provider-name {
  font-size: 1rem;
  font-weight: bold;
  margin: 0;
}

.provider-rating {
  display: flex;
  align-items: center;
  font-size: 0.9rem;
}

.provider-service-name {
  font-size: 0.9rem;
  color: #333;
  font-weight: bold;
}

.provider-address {
  font-size: 0.8rem;
  color: #666;
  margin-top: 0.5rem;
  max-width: 220px;
}

.service-card-body {
  display: flex;
  align-items: center;
  padding: 1rem;
}

.service-card-logo {
  flex-shrink: 0;
  margin-right: 1rem; 
}

.service-card-logo .logo-img {
  width: 50px; 
  height: 50px;
  border-radius: 50%;
  object-fit: cover; 
}

.service-details {
  flex-grow: 1; 
}

.service-card-footer {
  border-top: 1px solid #eee;
  display: flex;
  align-items: center;
  justify-content: space-between; 
  padding: 1rem 0.5rem;
}
.service-card-next-time {
  font-weight: bold;
  margin-right: 1rem;
  flex-shrink: 0;
}

.available-times {
  display: flex;
  gap: 0.3rem;
}

.time-slot {
  background-color: #CCD7DF;
  border-radius: 7px;
  padding: 6px 6px;
  font-size: 0.8rem;
}
</style>
