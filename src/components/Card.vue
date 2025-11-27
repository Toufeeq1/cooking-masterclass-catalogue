<script>
export default {
  name: 'CardComponent',
  props: {
    course: Object,
    isInWishlist: Boolean
  },
}
</script>

<template>
  <div class="card h-100">
    <div class="card-img-container">
      <img :src="course.image" class="card-img-top" alt="Course image" />
      <div v-if="!course.available" class="sold-out-overlay">
        <span class="badge bg-danger">Sold Out</span>
      </div>
    </div>

    <div class="card-body d-flex flex-column">
      <h5 class="card-title">{{ course.title }}</h5>
      <p class="card-text">
        Chef: {{ course.chef }} <br />
        Skill: {{ course.skillLevel }} <br />
        Price: {{ course.price }}
      </p>
      
      <button
        class="btn w-100 mt-auto"
        :class="isInWishlist ? 'btn-success' : 'btn-outline-primary'"
        :disabled="!course.available || isInWishlist"
        @click="$emit('save-course', course)"
      >
        {{ isInWishlist ? 'Added to Wishlist' : course.available ? 'Save to Wishlist' : 'Sold Out' }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.card {
  overflow: hidden;
  width: 100%;
}

.card-img-container {
  width: 100%;
  height: 200px;
  overflow: hidden;
  position: relative;
}

.card-img-top {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.sold-out-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.sold-out-overlay .badge {
  font-size: 1.2rem;
  padding: 0.5rem 1rem;
}

.card-body {
  min-height: 200px;
}
</style>