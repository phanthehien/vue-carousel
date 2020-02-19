<template>
  <div class="carousel-container">
    <navigation @next="handleNext" @prev="handlePrev" :disabled-prev="current===0" :disabled-next="current===items.length-1">
      <div class="carousel">
        <template v-for="(item, index) in items">
          <div 
            :key="index"
            :class="['carousel-item', { 'active': isActive(index) }]"
          >
            {{ item.text }}
          </div>
        </template>
      </div>
    </navigation>
    <pagination 
      :items="items" 
      :selected-item="selectedItem"
      @item-changed="handleItemChanged" 
    />
  </div>
</template>

<script>
import Pagination from "./pagination";
import Navigation from "./navigation";

export default {
  name: "Carousel",

  props: {
    items: Array
  },

  computed: {
    itemCount() {
      return this.items.length;
    },

    selectedItem() {
      return this.items[this.current];
    }
  },

  components: {
    Pagination,
    Navigation,
  },
  
  data() {
    return {
      current: 0
    };
  },

  methods: {
    handleNext() {
      this.current = (this.current < this.itemCount - 1) ? this.current + 1 : 0;
    },

    handlePrev() {
      this.current = this.current === 0 ? (this.itemCount - 1) : this.current - 1; 
    },

    isActive(index) {
      return this.current === index;
    },

    handleItemChanged(item) {
      this.current = this.items.indexOf(item);
    },
  }
  
};
</script>

<style scoped lang="scss">

.carousel {
  &-container {
    max-width: 800px;
    margin: 0 auto;
    padding-left: 50px;
    padding-right: 50px;
  }

  &-item {
    height: 350px;
    max-width: 100%;
    border-radius: 5px;
    
    overflow: hidden;
    display: none;
    justify-content: center;
    justify-items: center;
    align-items: center;

    -webkit-box-shadow: 10px 10px 20px 0 rgba(47, 94, 90, 0.2);
    -moz-box-shadow: 10px 10px 20px 0 rgba(47, 94, 90, 0.2);
    box-shadow: 10px 10px 20px 0 rgba(47, 94, 90, 0.2);

    &.active {
      display: flex;
      opacity: 1;
      background-color: lightgray;
      animation-name: scaleIn;
      animation-duration: 0.3s;
    }
  }
}

@keyframes fadeIn {
	0% {
		opacity: 0.5;
	}
	100% {
		opacity: 1;
	}
}

@keyframes scaleIn {
	0% {
    transform: scale(0.5);
	}
	90% {
		transform: scale(1.1);
	}
  100% {
		transform: scale(1);
	}
}


</style>
