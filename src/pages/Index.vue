<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1>Product page!</h1>

    <div v-if="$page.gcms.products">
      <div
        v-for="(product) in products"
        :key="product.id"
      >
        <g-link :to="'product/' + product.id" > {{product.name}} </g-link>
        <p> {{product.slug}}</p>
        <p> Description: {{product.description.markdown}}</p>
        <p> Price: ${{product.price}}</p>
        <p> Category: ${{product.category.name}}</p>
        <g-image v-for="(images, slug) in product.images" class="test" :key="slug" :src="images.url" width="200" height="200"  />       
      </div>
    </div>

  </Layout>
</template>

<script>
export default {

  data() {
    return {
      
      image: [],
      products: [{
        name: '',
        description: {
          markdown: ''
        },
        category: {
          name: ''
        },
        price: '',
        images: [{
          url: ''
        }]
      }],
    }
  },
 
 created(){
  this.products = this.$page.gcms.products
 },
 
 
}
</script>

<page-query>
  {
    gcms{
      products {
        id
        name
        description{
          markdown
        }
        category{
          name
        }
        price
        images {
          url
        }
        slug
      }
    }
  }

</page-query>


<style>
.home-links a {
  margin-right: 1rem;
}
.test{
  width: 300px;
}
</style>
