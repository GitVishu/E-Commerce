<template>
    <Navbar />
    <div class="order-container">
      
      <div class="order-summary">
        <h2>Order Summary</h2>
        <div v-if="cart.length">
          <ul class="order-list">
            <li v-for="(item, index) in cart" :key="index">
              <span>{{ item.name }}</span>
              <span>₹{{ item.price }}</span>
            </li>
          </ul>
          <hr />
          <div class="summary-details">
            <p>Subtotal: <span>₹{{ subtotal }}</span></p>
            <p>GST (18%): <span>₹{{ gst }}</span></p>
            <p class="total"><strong>Total: <span>₹{{ total }}</span></strong></p>
          </div>
          <div class="button-group">
            <button class="proceed-button" @click="proceedToCheckout">Proceed</button>
            <button class="clear-button" @click="clearCart">Clear Cart</button>
          </div>
        </div>
        <div v-else>
          <p class="empty-cart">Your cart is empty.</p>
        </div>
      </div>
    </div>
    <MainFooter/>
  </template>
  
  <script>
  import Navbar from "../components/Navbar.vue";
  import MainFooter from "../components/MainFooter.vue"
  
  export default {
    name:"Order",
    components: {
      Navbar,
      MainFooter
    },
    data() {
      return {
        cart: [],
      };
    },
    computed: {
      subtotal() {
        return this.cart.reduce((acc, item) => acc + item.price, 0).toFixed(2);
      },
      gst() {
        return (this.subtotal * 0.18).toFixed(2);
      },
      total() {
        return (parseFloat(this.subtotal) + parseFloat(this.gst)).toFixed(2);
      },
    },
    mounted() {
      this.cart = JSON.parse(sessionStorage.getItem("cart")) || [];
    },
    methods: {
      proceedToCheckout() {
        alert(`Proceeding to checkout. Total amount: ₹${this.total}`);
        // Add your checkout logic here (e.g., redirect to a payment page)
      },
      clearCart() {
        this.cart = [];
        sessionStorage.removeItem("cart");
      },
    },
  };
  </script>
  
  <style scoped>
  /* General container styling */
  .order-container {
    max-width: 800px;
    margin: 40px auto;
    padding: 20px;
    border: 1px solid #e5e5e5;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    background-color: #ffffff;
  }
  
  /* Order summary heading */
  .order-summary h2 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
    font-size: 1.8rem;
  }
  
  /* Order list styling */
  .order-list {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }
  .order-list li {
    display: flex;
    justify-content: space-between;
    padding: 10px 0;
    border-bottom: 1px solid #e5e5e5;
  }
  .order-list li span {
    font-size: 1.1rem;
    color: #444;
  }
  
  /* Summary details */
  .summary-details {
    margin-top: 20px;
    font-size: 1.2rem;
  }
  .summary-details p {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
  }
  .summary-details .total {
    font-size: 1.4rem;
    font-weight: bold;
    color: #e67e22;
  }
  
  /* Button group styling */
  .button-group {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }
  
  /* Proceed button styling */
  .proceed-button {
    flex: 1;
    margin-right: 10px;
    padding: 12px;
    background-color: #27ae60;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1.1rem;
    transition: background-color 0.3s ease;
  }
  .proceed-button:hover {
    background-color: #219150;
  }
  
  /* Clear cart button styling */
  .clear-button {
    flex: 1;
    margin-left: 10px;
    padding: 12px;
    background-color: #e74c3c;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1.1rem;
    transition: background-color 0.3s ease;
  }
  .clear-button:hover {
    background-color: #c0392b;
  }
  
  /* Empty cart message */
  .empty-cart {
    text-align: center;
    color: #888;
    font-size: 1.2rem;
    margin-top: 40px;
  }
  
  /* Responsive design */
  @media (max-width: 600px) {
    .order-container {
      padding: 15px;
    }
    .order-summary h2 {
      font-size: 1.5rem;
    }
    .summary-details p,
    .order-list li {
      font-size: 1rem;
    }
    .button-group {
      flex-direction: column;
    }
    .proceed-button,
    .clear-button {
      margin: 10px 0;
    }
  }
  </style>
  