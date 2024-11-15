<template>
  <div class="card">
    <div class="card-image">
      <img :src="product.image" alt="Product Image" class="card-image" />
    </div>
    <h3>{{ product.name }}</h3>
    <div class="description">
      <p>Description: {{ product.description }}</p>
    </div>

    <div class="price">
      <p>Price: ₹{{ product.price }}</p>
    </div>
    <button @click="addToCart">Add to Cart</button>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: ["product"],
  methods: {
    addToCart() {
      // Retrieve the current cart from sessionStorage or initialize it as an empty array
      const cart = JSON.parse(sessionStorage.getItem("cart")) || [];

      // Add the current product to the cart
      cart.push(this.product);

      // Save the updated cart back to sessionStorage
      sessionStorage.setItem("cart", JSON.stringify(cart));

      alert(`${this.product.name} added to cart!`);
    },
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
/* Card container */
.card {
  background-color: #ffffff;
  border: 1px solid #e5e5e5;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  overflow: hidden;
  position: relative;

  /* display: flex;
  flex-direction: column;
  justify-content: space-between; */
  transition: 0.3s;
}

/* Card hover effect */
.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.card-image {
  width: 100%;
  height: 40vh;
  border-radius: 8px;
  margin-bottom: 20px;
  display: grid;
  place-items: center;
}

/* Product name styling */
h3 {
  
  font-size: 1.5rem;
  color: #4e4537;
  margin-bottom: 10px;
}

/* Description styling */
.description {
  color:#4e4537;
  font-size: 1rem;
  
}

/* Price styling */
.price {
  font-size: 1.2rem;
  color:  #048289 ;
  margin-bottom: 10px;
  font-weight: bold;
}

/* Add to Cart button styling */
button {
  background-color:  #03684f;
  color: #ffffff;
  padding: 10px 20px;
  border-radius: 5px;
  text-decoration: none;
  display: inline-block;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

button:hover {
  cursor: pointer;
  background-color:  #008765;
}

/* Responsive styling for small screens */
@media (max-width: 768px) {
  .card {
    padding: 15px;
  }
}
</style>
