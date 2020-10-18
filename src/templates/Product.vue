<template>
    <Layout>
        <div v-if="this.$page.gcms.product">
            <h1> {{ product.name }} </h1>
            <p > {{ product.description.markdown }} </p>
            <g-image :src="product.images[0].url" alt="new image" />
            <p>
                ${{ product.price}}
            </p>
            
        </div>
    </Layout>
</template>

<script>
export default {
    data() {
        return {
            product: {
                name: '',
                description: {
                    markdown: ''
                },
                images: [{
                    url: ''
                }]

            }
        
        }
    },
    created(){
        this.product = this.$page.gcms.product
        console.log('Product here', this.product)
    }
}  
</script>

<page-query>
query GetProduct($id: ID) {
    gcms {
        product(where: {id: $id}) {
                id
            name
            description{
                markdown
            }
            price
            images{
                url
            }
        }
    }
}
</page-query>