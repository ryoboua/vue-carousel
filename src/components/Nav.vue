<template>
  <div class="nav">
    <ul>
      <li v-for="(l, i) in navLabels" :key="i">{{ l }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navLabels: ["All", "Photography", "Fashion", "Sculpture"],
    }
  },
}
</script>

<style>
.nav {
  display: flex;
  justify-content: center;
  width: 100%;
}

.nav ul {
  display: flex;
  list-style-type: none;
  padding: 0%;
}

.nav ul li,
.nav ul li:hover {
  margin: 0 10px;
  padding: 5px 18px;
}
.nav ul li:hover {
  background-color: #f4efe5;
  border-radius: 5px;
  cursor: pointer;
}
</style>
