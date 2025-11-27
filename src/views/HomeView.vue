<script>
import CardComponent from '../components/Card.vue'
import courses from '../data/courses.js'

export default {
  name: 'CoursesPage',
  components: { CardComponent },
  props: {
    wishlist: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return { 
      courses 
    }
  },
  methods: {
    isInWishlist(courseId) {
      return this.wishlist.some(item => item.id === courseId)
    }
  }
}
</script>

<template>
  <div class="container">
    <div class="row g-4">
      <div 
        v-for="course in courses" 
        :key="course.id"
        class="col-12 col-sm-6 col-lg-4 col-xl-3"
      >
        <CardComponent 
          :course="course"
          :isInWishlist="isInWishlist(course.id)"
          @save-course="$emit('save-course', course)"
        />
      </div>
    </div>
  </div>
</template>