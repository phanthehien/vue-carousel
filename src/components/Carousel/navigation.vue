<template>
  <div class="navigation">
    <div :class="['navigation-item noselect prev', { disabled: disabledPrev }]"> 
      <a @click="handlePrev"> 
        <span>&#60;</span> 
      </a>
    </div>
    <div class="container">
      <slot />
    </div>
    <div :class="['navigation-item noselect next', { disabled: disabledNext }]"> 
      <a @click="handleNext"> 
        <span>&#62;</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Navigation',
  
  props: {
    disabledNext: {
      type: Boolean,
      default: false,
    },
    disabledPrev:  {
      type: Boolean,
      default: false,
    },
  },

  methods: {
    handlePrev() {
      this.$emit('prev');
    },
    
    handleNext() {
      this.$emit('next');
    }
  }
}
</script>

<style>
.navigation {
  display: flex;
  flex-direction: row;
  align-items: center
}

.container {
  flex-grow: 1;
}

.navigation-item {
  width: 44px;
  display: block;
  cursor: pointer;
  padding: 10px;
}

.navigation-item a {
  display: block;
  border: solid 1px gray;
  font-size: 24pt;
  font-weight: bolder;
  width: 44px;
  height: 44px;
  border-radius: 5px;
}

.navigation-item a:hover {
  background-color: green;
  color: yellow;
}

.navigation-item:hover {
  transform: scale(1.1); 
}

.disabled {
  cursor: none;
  pointer-events: none;
  opacity: 0.5;
}

.noselect {
  -webkit-touch-callout: none;
    -webkit-user-select: none;
     -khtml-user-select: none;
       -moz-user-select: none;
        -ms-user-select: none;
            user-select: none;
}

</style>