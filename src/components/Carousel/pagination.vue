<template>
  <nav class="pagination">
    <ul>
      <template v-for="(item, index) in items">
        <li 
          :key="index" 
          :class="{ 'active': isActive(item) }"
          @click="handleClick(item)"
        >
          <a><span> {{ index + 1 }} </span></a>
        </li>
      </template>
    </ul>
  </nav>
</template>
<script>
export default {
  name: "Pagination",  
  
  props: {
    items: Array,
    selectedItem: Object,
  },

  methods: {
    handleClick(item) {
      if (this.selectedItem !== item) {
        this.$emit('item-changed', item);
      }
    },

    isActive(item) {
      return this.selectedItem === item;
    }
  }
};
</script>

<style scoped>
.pagination {
  width: 100%;
}

.pagination ul {
  list-style: none;
  justify-content: center;
  display: flex;
}

.pagination li {
  cursor: pointer;
  margin: 5px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: solid 2px gray;
  display: flex;
  align-items: center;
}

.pagination li:hover {
  transform: scale(1.1);
}

.pagination li.active {
  border-color: green;
  background-color: antiquewhite;
}

.pagination a {
  flex-basis: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.pagination span {
  display: block;
  width: 100%;
}

.noselect {
  -webkit-touch-callout: none;
    -webkit-user-select: none;
     -khtml-user-select: none;
       -moz-user-select: none;
        -ms-user-select: none;
            user-select: none;
}
</style>>