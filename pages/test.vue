<template>
  <div class="container">
    <div class="gallery">
      <div
        v-for="(img, idx) in imgs"
        :key="idx"
        class="pic"
        @click="() => show(idx)"
      >
        <img :src="img.src ? img.src : img">
      </div>
    </div>

    <client-only>
      <vue-easy-lightbox
        :visible="visible"
        :index="index"
        :imgs="imgs"
        @hide="visible = false"
        @on-prev="handlePrev"
        @on-next="handleNext"
      />
    </client-only>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        imgs: [
          'https://via.placeholder.com/250.png/09f/fff?text=first+img',
          'https://via.placeholder.com/250.png/09f/fff?text=second+img',
          'https://via.placeholder.com/250.png/09f/fff?text=third+img'
        ],
        visible: false,
        index: 0 // default
      }
    },
    methods: {
      show(index) {
        this.index = index
        this.visible = true
      },
      handlePrev(oldIndex, newIndex) {
        console.log('when next btn click ----')
        console.log('oldIndex of imgs:', oldIndex)
        console.log('newIndex of imgs:', newIndex)
      },
      handleNext(oldIndex, newIndex) {
        console.log('when next btn click ----')
        console.log('oldIndex of imgs:', oldIndex)
        console.log('newIndex of imgs:', newIndex)
      },
    }
  }
</script>

<style scoped>
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .gallery {
    display: flex;
  }

  .pic {
    cursor: pointer;
    margin-right: 8px;
  }
</style>