<template>
  <div id="app">
    <div class="container">
    <app-header></app-header>
    <router-view/>
    </div>
    <app-footer></app-footer>
  </div>
</template>
<script>
  import AppHeader from '@/components/AppHeader'
  import AppFooter from '@/components/AppFooter'
  export default {
    components: {
      AppHeader,
      AppFooter
    }
  }
</script>
