<template>
  <div class="center examplex">
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
