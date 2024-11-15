<template>
  <Navbar />
  
  <div class="products-container">
    <h1>Our Products</h1>

    <!-- Category Filter -->
    <div class="category-filter">
      <button
        v-for="category in categories"
        :key="category"
        :class="{ active: selectedCategory === category }"
        @click="selectedCategory = category"
      >
        {{ category }}
      </button>
    </div>

    <!-- Products Grid -->
    <div class="products-grid">
      <ProductCard
        v-for="(product, index) in filteredProducts"
        :key="index"
        :product="product"
      />
    </div>
  </div>
  <MainFooter/>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import ProductCard from "../components/ProductCard.vue";
import MainFooter from "../components/MainFooter.vue";

export default {
  name: "Products",
  components: {
    Navbar,
    ProductCard,
    MainFooter
  },
  data() {
    return {
      selectedCategory: "All",
      categories: ["All", "Cloth", "Electronics", "Furniture"], // Define categories
      products: [
        { name: "Product 1", price: 500, description: "Amazing product 1", category: "Cloth", image: require("@/assets/cloth1.jpg")},
        { name: "Product 2", price: 1000, description: "Amazing product 2", category: "Electronics", image:require("@/assets/electronics1.jpg") },
        { name: "Product 3", price: 1500, description: "Amazing product 3", category: "Furniture", image: require("@/assets/furniture1.jpg")},
        { name: "Product 4", price: 2000, description: "Amazing product 4", category: "Cloth", image:require("@/assets/cloth2.jpg") },
        { name: "Product 5", price: 2500, description: "Amazing product 5", category: "Electronics", image:require("@/assets/electronics2.jpg") },
        { name: "Product 6", price: 3000, description: "Amazing product 6", category: "Furniture", image:require("@/assets/furniture2.jpg") },
        { name: "Product 7", price: 500, description: "Amazing product 1", category: "Cloth", image:require("@/assets/cloth3.jpg") },
        { name: "Product 8", price: 1000, description: "Amazing product 2", category: "Electronics", image:require("@/assets/electronics3.jpg") },
        { name: "Product 9", price: 1500, description: "Amazing product 3", category: "Furniture" , image:require("@/assets/furniture3.jpg")},
        { name: "Product 10", price: 2000, description: "Amazing product 4", category: "Cloth" , image:require("@/assets/cloth4.jpg")},
        { name: "Product 11", price: 2500, description: "Amazing product 5", category: "Electronics", image:require("@/assets/electronics4.jpg") },
        { name: "Product 12", price: 3000, description: "Amazing product 6", category: "Furniture", image:require("@/assets/furniture4.jpg") },
      ],
    };
  },
  computed: {
    filteredProducts() {
      if (this.selectedCategory === "All") {
        return this.products;
      }
      return this.products.filter(product => product.category === this.selectedCategory);
    },
  },
};
</script>

<style scoped>
/* Container styling */
.products-container {
  max-width: 1200px;
  margin: 40px auto;
  padding: 20px;
  text-align: center;
}

/* Page heading */
h1 {
  font-size: 2.5rem;
  margin-bottom: 40px;
  color:#025661;
  text-transform: uppercase;
}


/* Product grid styling */
.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  /* padding: 0 20px; */
}

/* Category filter styling */
.category-filter {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  margin-bottom: 20px;
}

.category-filter button {
  padding: 10px 20px;
  margin: 5px 0;
  background-color: #ecf0f1;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  color: #504c2c;
  border-radius: 4px;
  transition: background-color 0.3s;
}

.category-filter button.active,
.category-filter button:hover {
  background-color: #008765;;
  color: white;
}

/* Responsive adjustments for small screens */
@media (max-width: 600px) {
  .category-filter {
    flex-direction: column;
  }
  
  .category-filter button {
    width: 100%;
    text-align: center;
  }
}

</style>
