<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <NavBar/>
    <AdminItem/>
  </div>
</template>

<script>
// @ is an alias to /src
import NavBar from '@/components/NavBar.vue'
import AdminItem from '@/components/AdminItem.vue'
export default {
  name: 'home',
  components: {
    NavBar,
    AdminItem
  }
}
</script>
