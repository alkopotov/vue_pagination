<template>
  <section class="pagination_wrapper">
    <div @click="$emit('decrPage')" class="side_button"> 
      <svg width="7" height="12" fill="none" viewBox="0 0 7 12" xmlns="http://www.w3.org/2000/svg">
        <path d="M0.22 6.71997C0.0793075 6.57946 0.000175052 6.38882 0 6.18997V5.80997C0.00230401 5.61156 0.081116 5.4217 0.22 5.27997L5.36 0.149974C5.45388 0.055318 5.58168 0.0020752 5.715 0.0020752C5.84832 0.0020752 5.97612 0.055318 6.07 0.149974L6.78 0.859974C6.87406 0.952138 6.92707 1.07828 6.92707 1.20997C6.92707 1.34166 6.87406 1.46781 6.78 1.55997L2.33 5.99997L6.78 10.44C6.87466 10.5339 6.9279 10.6617 6.9279 10.795C6.9279 10.9283 6.87466 11.0561 6.78 11.15L6.07 11.85C5.97612 11.9446 5.84832 11.9979 5.715 11.9979C5.58168 11.9979 5.45388 11.9446 5.36 11.85L0.22 6.71997Z" :class="current > 1 ? 'side_icon_active ' : 'side_icon'"/>
      </svg>
    </div>
    <div
      v-for="elem in maxPages" 
      :key="elem" 
      @click="setCurrentPage(elem)"
      :class="elem === current ? 'page_button active' : 'page_button'"
    >{{ elem }}
    </div>
    <div @click="$emit('incrPage')" class="side_button"> 
      <svg width="7" height="12" viewBox="0 0 7 12" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M6.78 6.71997C6.92069 6.57946 6.99982 6.38882 7 6.18997V5.80997C6.9977 5.61156 6.91888 5.4217 6.78 5.27997L1.64 0.149974C1.54612 0.055318 1.41832 0.0020752 1.285 0.0020752C1.15168 0.0020752 1.02388 0.055318 0.93 0.149974L0.22 0.859974C0.125936 0.952138 0.0729284 1.07828 0.0729284 1.20997C0.0729284 1.34166 0.125936 1.46781 0.22 1.55997L4.67 5.99997L0.22 10.44C0.125343 10.5339 0.0721006 10.6617 0.0721006 10.795C0.0721006 10.9283 0.125343 11.0561 0.22 11.15L0.93 11.85C1.02388 11.9446 1.15168 11.9979 1.285 11.9979C1.41832 11.9979 1.54612 11.9446 1.64 11.85L6.78 6.71997Z" :class="current < maxPages ? 'side_icon_active ' : 'side_icon'"/>
      </svg>
    </div>

  </section>

</template>


<script setup>
  const {current, maxPages} = defineProps({
    current: Number,
    maxPages: Number
  })

  const emit = defineEmits(['incrPage', 'decrPage', 'setPage'])

  function setCurrentPage(page){
    emit('setPage', page)
  } 
</script>

<style>
  .pagination_wrapper {
    display: flex;
    gap: 20px;
    margin: auto;
    width: fit-content;
    margin-top: 52px;
  }

  .side_icon {
    fill: #BCBCBC;
  }
  .side_icon_active {
    fill: #185BC3;
  }

  .side_button, .page_button {
    width: 64px;
    height: 64px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    border: 1px solid #BDBDBD;
    border-radius: 6px;
    font-family: Inter;
    font-size: 18px;
    font-weight: 800;
    line-height: 22px;
    letter-spacing: 0em;
    text-align: center;
    color: #BDBDBD;
  }

  .page_button.active {
    background-color: blue;
    color: white;
  }
</style>