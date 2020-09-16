<template>
  <div width="330" height="300">
    <h1>Test</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { title: "Home", icon: "dashboard" },
        { title: "About", icon: "question_answer" }
      ],
      links: ["Home", "Contacts", "Settings"],
      mini: true
    }
  }
}
</script>

<style></style>
