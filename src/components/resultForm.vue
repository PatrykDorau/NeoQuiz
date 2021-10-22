<template>
  <div>
      <h1>wynik:</h1>
      <div
        v-for="(product, i) in filteredProductsArray"
        :key="i"
      >
        <productForm
          :name="product.name"
          :picture="product.picture"
        />
      </div>
  </div>
</template>

<script>
import productForm from './productForm.vue'
export default {
    name: 'resultForm',
    props: {
      productsArray: Array,
      resultsArray: Array
    },
    components: {
      productForm
    },
    data(){
      return {
        filteredProductsArray: [],
        uniqueResults:[]
      }
    },
    created(){
      this.uniqueResults = [...new Set(this.resultsArray)]
      console.log(this.uniqueResults,'unique')
      for(let i = 0; i < this.productsArray.length; i++){
        console.log(this.productsArray[i].key, "iteracja")
        if(JSON.stringify(this.productsArray[i].key) === JSON.stringify(this.uniqueResults)){
          this.filteredProductsArray.push(this.productsArray[i])
        }
      }
      console.log(this.filteredProductsArray,'filtered products')
    }
    // created(){
    //   this.uniqueResults = [...new Set(this.resultsArray)]
    //   console.log(this.uniqueResults,'unique')
    //   for(let i = 0; i<this.productsArray.length; i++){
    //     for(let x = 0; x<this.productsArray.key.length; x++){
    //       for(let z = 0; z<this.uniqueResults.length; z++){
    //         if(this.productsArray[i].key[x] === this.uniqueResults[z]){
    //           this.filteredProductsArray.push(this.productsArray[i])
    //         }
    //       }
    //     }
    //   }
    //   console.log(this.filteredProductsArray,'filtered products')
    // }

}
</script>

<style>

</style>