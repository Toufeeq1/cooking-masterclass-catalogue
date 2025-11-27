<script>
import NavbarComponent from './components/Navbar.vue'
import HomeView from './views/HomeView.vue'

export default {
  components: {
    NavbarComponent,
    HomeView
  },

  data() {
    return {
      wishlist: []
    }
  },

  methods: {
    addToWishlist(course) {

      const exists = this.wishlist.find(c => c.id === course.id)
      if (!exists) {
        this.wishlist.push(course)
      }
    },

    openWishlist() {
      this.$refs.wishlistModal.showModal()
    }
  }
}
</script>

<template>
  <NavbarComponent 
    :count="wishlist.length" 
    @open-wishlist="openWishlist"
  />

  <div class="container-fluid px-4">
    <HomeView 
      :wishlist="wishlist"
      @save-course="addToWishlist"
    />
  </div>

  <dialog ref="wishlistModal" class="wishlist-modal">
    <h2>Your Saved Courses</h2>

    <div v-if="wishlist.length === 0" class="p-3">
      <p>No courses saved yet.</p>
    </div>

    <ul v-else>
      <li v-for="item in wishlist" :key="item.id">
        {{ item.title }} — {{ item.chef }} — {{ item.price }}
      </li>
    </ul>

    <button class="btn btn-secondary mt-3" @click="$refs.wishlistModal.close()">
      Close
    </button>
  </dialog>
</template>

<style scoped>
.wishlist-modal {
  padding: 20px;
  border-radius: 10px;
  border: none;
  width: 400px;
}
</style>