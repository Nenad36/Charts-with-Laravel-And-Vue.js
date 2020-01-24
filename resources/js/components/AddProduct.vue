<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-12">
                <div class="card">
                    <div class="card-body">
                        <form @submit.prevent="createProduct">
                            <div class="form-group">
                                <label for="name">Name</label>
                                <input type="text" id="name" class="form-control" v-model="product.name">
                            </div>
                            <div class="form-group">
                                <label for="year">Year</label>
                                <input type="number" id="year" class="form-control" v-model="product.year">
                            </div>
                            <div class="form-group">
                                <label for="price">Price</label>
                                <input type="number" id="price" class="form-control" v-model="product.price">
                            </div>
                            <div class="form-group">
                                <button class="btn btn-primary">Create Product</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "AddProduct",
        data(){
            return {
                product: {}
            }
        },
        methods: {
            createProduct(){
                let uri = 'http://charts.test/products';
                axios.post(uri, this.product).then((response)=>{
                    window.location.reload();
                });
            }
        }
    }
</script>

<style scoped>

</style>