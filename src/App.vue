<template>

  <div class="container border border-1 mt-3">
    
    <!-- Header -->
    <div class="row mt-2">
      
      <div class="col-12">
        <HeaderComponent/>
      </div>
      
    </div>

    <!-- Links & Body -->
    <div class="row mt-2">

        <div class="col-4">
          <LinksComponent/>
        </div>          
      
        <div class="col-8">
          <ProductComponent/>
        </div>
      
    </div>

    <!-- footer -->
    <div class="row mt-2 mb-2">

      <div class="col-12">
        <FooterComponent/>
      </div>
    
    </div>
  
  </div>

</template>

<script>
  import HeaderComponent from './components/HeaderComponent.vue';
  import LinksComponent from './components/LinksComponent.vue';
  import ProductComponent from './components/ProductComponent.vue';
  import FooterComponent from './components/FooterComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    LinksComponent,
    ProductComponent,
    FooterComponent
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
