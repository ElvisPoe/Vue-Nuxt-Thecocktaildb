<template>
  <div class="center examplex mt-3">
    <vs-button flat icon @click="openNotification(null, 'primary')">
      Here is my suggestion
    </vs-button>
  </div>
</template>
<script>
export default {
  methods: {
    openNotification(position = null, color) {
      const noti = this.$vs.notification({
        color,
        position,
        title: 'A cocktail suggestion - By Poe',
        text: 'Random cocktail picked up as a suggestion. Surprisingly the best cocktails are shown!'
      })
    }
  }
}
</script>
<style>
.mt-3 {
 margin-top: 3rem;
}
</style>
