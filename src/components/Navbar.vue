<script>
export default {
  name: 'NavbarComponent',
  props: {
    count: Number,
  },
  emits: ['open-wishlist'],
  data() {
    return {
      isMenuOpen: false
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen
    }
  }
}
</script>

<template>
  <nav class="navbar navbar-expand-lg custom-navbar">
    <div class="container-fluid">
      <a class="navbar-brand" href="#"> <i class="bi bi-cake fs-3"></i> Cooking Masterclass </a>

      <button
        class="navbar-toggler"
        type="button"
        @click="toggleMenu"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" :class="{ show: isMenuOpen }" id="navbarNavAltMarkup">
        <div class="navbar-nav ms-auto">
          <a class="nav-link" href="#">Home</a>
          <a class="nav-link" href="#">Courses</a>
          <a class="nav-link" href="#">About</a>
        </div>

        <div
          class="wishlist-box d-flex align-items-center ms-lg-3 my-2 my-lg-0"
          @click="$emit('open-wishlist')"
          style="cursor: pointer"
        >
          <i class="bi bi-heart-fill wishlist-icon"></i>
          <span class="wishlist-count">{{ count }}</span>
        </div>

        <form class="d-flex ms-lg-3 mt-2 mt-lg-0" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" />
          <button class="btn btn-outline-sweet" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.custom-navbar {
  background-color: var(--color-primary);
  margin-bottom: 20px;
}

.custom-navbar .navbar-brand,
.custom-navbar .nav-link,
.custom-navbar .btn {
  color: var(--color-light);
}

.custom-navbar .nav-link:hover {
  color: var(--color-accent);
}

.btn-outline-sweet {
  border: 2px solid var(--color-light);
  color: var(--color-light);
  background-color: transparent;
  transition: all 0.3s ease;
}

.btn-outline-sweet:hover {
  background-color: var(--color-light);
  color: var(--color-primary);
  border-color: var(--color-light);
}

.wishlist-box {
  background: var(--color-accent);
  padding: 6px 12px;
  border-radius: 20px;
}

.wishlist-icon {
  font-size: 1.2rem;
  color: var(--color-primary);
}

.wishlist-count {
  font-weight: bold;
  margin-left: 6px;
  color: var(--color-primary);
}

@media (max-width: 767px) {
  .wishlist-box {
    width: fit-content;
  }
  
  .navbar-collapse {
    text-align: center;
  }
}
</style>