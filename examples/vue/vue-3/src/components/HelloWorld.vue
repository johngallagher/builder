<template>
  <div class="hello-world">
    <div v-html="ftchedHtml"></div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: 'world',
    },
  },
  data() {
    return {
      fetchedHtml: '',
    };
  },
  mounted() {
    fetch('https://www.biggerpockets.com/shared_components/component?name=membership/dashboard/widgets/trending_topics')
      .then(response => response.text())
      .then(html => {
        this.fetchedHtml = html;
      })
      .catch(error => {
        console.error('Error fetching HTML:', error);
      });
  }
};
</script>

<style scoped>
.hello-world {
  display: flex;
  flex-direction: column;
}
.text {
  padding: 50px;
}
</style>
