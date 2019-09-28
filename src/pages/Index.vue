<template>
  <Layout>
    <section>
      <g-link
        v-for="edge in $page.allProduct.edges"
        :key="edge.node.id"
        :to="edge.node.path"
        class="product"
      >
        <ProductPreview :product="edge.node" />
      </g-link>
    </section>
  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: "Hello, world!"
  }
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
