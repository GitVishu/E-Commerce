<template>
  <nav class="navbar">
    <div class="logo">
      <span class="logo-text" style="font-size: 25px;  color:#025661;"><b>E-COMMERCE</b></span>
    </div>
    <!-- Hamburger Button -->
    <button class="hamburger" @click="toggleMenu">
      <span :class="{ 'hamburger-top': isOpen }"></span>
      <span :class="{ 'hamburger-middle': isOpen }"></span>
      <span :class="{ 'hamburger-bottom': isOpen }"></span>
    </button>
    <!-- Navigation Links -->
    <ul :class="{ 'nav-links': true, 'dropdown-active': isOpen }">
      <li><router-link to="/" @click="closeMenu">Home</router-link></li>
      <li><router-link to="/products" @click="closeMenu">Products</router-link></li>
      <li><router-link to="/order" @click="closeMenu">Order</router-link></li>
      <li><router-link to="/contact" @click="closeMenu">Contact Us</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleMenu() {
      this.isOpen = !this.isOpen;
    },
    closeMenu() {
      this.isOpen = false;
    },
  },
};
</script>

<style scoped>
/* Navbar styles */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background-color:#e6e6fa;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  position: relative;
  z-index: 10;
}

.logo {
  display: flex;
  align-items: center;
}

/* Hamburger Menu Styles */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  height: 24px;
  background: transparent;
  border: none;
  cursor: pointer;
  z-index: 20;
}

.hamburger span {
  display: block;
  width: 25px;
  height: 3px;
  background-color: #333;
  transition: all 0.3s ease;
}

/* Hamburger Animations */
.hamburger-top {
  transform: rotate(45deg) translate(5px, 5px);
}

.hamburger-middle {
  opacity: 0;
}

.hamburger-bottom {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Nav links for desktop */
.nav-links {
  display: flex;
  list-style: none;
  gap: 25px;
}

.nav-links li {
  font-size: 22px;
}

.nav-links a {
  text-decoration: none;
  color: #333;
  transition: color 0.3s ease;
}

.nav-links a:hover,
.nav-links a.router-link-exact-active {
  color:#025661; /* Highlight color */
}

/* Media queries for responsive design */
@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .nav-links {
    display: none;
    position: absolute;
    top: 50px;
    right: 0;
    left: 0;
    background-color: #fff;
    align-items: center;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-top: 1px solid #eee;
    padding: 0;
  }

  .dropdown-active {
    display: flex;
    flex-direction: column;
  }

  .nav-links li {
    padding: 10px 20px; 
    border-bottom: 1px solid #eee;
    width:90%;
    text-align: center;
  }

  .nav-links li:last-child {
    border-bottom: none;
  }
}
</style>

