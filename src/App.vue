<template>
  <div id="app">
    <div class="container">
    <app-header></app-header>
    <app-footer></app-footer>
    </div>
    <router-view/>
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
