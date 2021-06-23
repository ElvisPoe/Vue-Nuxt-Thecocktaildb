<template>
  <div class="center">
    <vs-button flat icon @click="openNotification(null, 'primary')">
      <i class='bx bx-border-radius b-r'></i>
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
        title: 'Documentation Vuesax 4.0+',
        text: 'These documents refer to the latest version of vuesax (4.0+), to see the documents of the previous versions you can do it here 👉 Vuesax 3.x'
      })
    }
  }
}
</script>
