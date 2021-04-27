<template>
    <div>
        <form @submit.prevent="addProduct">
            <div class="form-group">
                <label>Kategori</label>
                <input v-model="product.categoryId" type="text" class="form-control"/>
            </div>
            <div class="form-group">
                <label>Ürün adı</label>
                <input v-model="product.name" type="text" class="form-control"/>
            </div>
            <div class="form-group">
                <label>Birim Fiyatı</label>
                <input v-model="product.unitPrice" type="text" class="form-control"/>
            </div>
            <div class="form-group">
                <label>Stok adedi</label>
                <input v-model="product.unitsInStock" type="text" class="form-control"/>
            </div>
            <button class="btn btn-success" type="submit">Ekle</button>
        </form>
    </div>
</template>
<script>
export default {
    data() {
        return {
            product:{categoryId:1, name:"", unitPrice:0, unitsInStock:0}
        }
    },
    methods:{
       async addProduct(){
            const result = await fetch("http://localhost:3000/products",{
                method:"POST",
                body:JSON.stringify(this.product),
                headers:{"Content-Type":"application/json"}
            })

            console.log(result)
        }
    }
}
</script>
<style>
    
</style>