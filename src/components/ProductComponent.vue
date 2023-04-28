<template>

    <table class="table table-striped table-bordered text-center" v-if="isNotActive==false">
        
        <thead>
        
            <tr>
                <th>ID</th>
                <th>Title</th>
                <th>Price</th>
                <th>discountPercentage</th>
                <th>Delete</th>
            </tr>
        
        </thead>
        
        <tbody v-for="product in productList" :key="product.id">
            
            <tr>
                <td>{{product.id}}</td>
                <td>{{product.title}}</td>
                <td>{{product.price}}</td>
                <td>{{product.discountPercentage}}</td>
                <td><button class="btn btn-danger border" @click="removeProduct(product.id)">X</button></td>
            </tr>

        </tbody>
        
    </table>
    

<button type="button" class="btn btn-secondary w-50 rounded-2" data-bs-toggle="modal" data-bs-target="#exampleModal"> Add Product </button>

<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalLabel">Modal title</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <form>
          <div class="field">
            <label class="label">Title</label>
            <div class="control">
              <input class="input" type="text" v-model="newProduct.title" required>
            </div>
          </div>
          <div class="field">
            <label class="label">Price</label>
            <div class="control">
              <input class="input" type="number" v-model="newProduct.price" required>
            </div>
          </div>
          <div class="field">
            <label class="label">Quantity</label>
            <div class="control">
              <input type="number" v-model="newProduct.quantity" required/>
            </div>
          </div>
          <div class="field">
            <label class="label">Discount Percentage</label>
            <div class="control">
              <input type="number" v-model="newProduct.discountPercentage" required/>
            </div>
          </div>
        </form>
    </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="addProduct">Save</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>

    import Products from '../../products';
    export default {
        data:()=>({
            isNotActive: false,
            newProduct:{
                title:"",
                price:'',
                quantity:'',
                total:'',
                discountPercentage:'',
                discountedPrice:'',
            },
            productList:Products
        }),
        methods: {
            addProduct(){
                const highestId = Math.max(...this.productList.map(product => product.id))
                const newId = highestId + 1
                const newProduct = { id: newId, ...this.newProduct };
                console.log(newProduct)
                if( this.newProduct.title.trim().length == 0 ) { return alert('Please enter a title for the new product'); }
                if(this.newProduct.price.toString().trim().length == 0) {return alert('Please enter a price for the new product')};
                if(this.newProduct.quantity.trim().length == 0) {return alert('Please enter a quantity for the new product')};
                if(this.newProduct.discountPercentage.trim().length == 0) {return alert('Please enter a discount percentage for the new product')};
                this.productList.push(newProduct);
                this.newProduct = {
                  title: null,
                  price: null,
                  quantity: null,
                  discountPercentage: null,
                };
                this.isNotActive = false;
            },
            removeProduct(id){
                this.productList = this.productList.filter(product => product.id !== id)
            },
            validate () {
                    'use strict'
                    const form = document.querySelector('.needs-validation')
                    if (!form.checkValidity()) {
                        form.classList.add('was-validated')
                        event.preventDefault()
                        event.stopPropagation()
                        console.log("success");
                    }else{
                        this.isNotActive=true;
                    }
                }
        },
        components: {},
        computed: {}
    };

</script>

<style>

</style>