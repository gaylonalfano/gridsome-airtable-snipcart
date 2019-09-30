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
    <Pager :info="$page.allProduct.pageInfo" linkClass="pager" />
  </Layout>
</template>

<page-query>
query Products ($page: Int) {
  allProduct (perPage: 6, page: $page) @paginate {
    pageInfo {
      totalPages,
      currentPage
    }
    edges {
      node {
        id,
        title,
        path,
        price,
        content,
        fields {
          Images {
            thumbnails {
              large {
                url
              }
            }
          }
        }
      }
    }
  }
}
</page-query>

<script>
import { Pageer } from "gridsome";
import ProductPreview from "../components/ProductPreview";
export default {
  components: {
    Pager,
    ProductPreview
  },
  metaInfo: {
    title: "Gridsome Airtable Snipcart"
  }
};
</script>

<style>
.product-navigation {
  display: flex;
  justify-content: center;
  flex: 0 1 auto;
}
.product-navigation a {
  box-sizing: border-box;
  width: 2em;
  background-color: #e3e3e3;
  color: black;
  font-weight: bold;
  margin: 0.5em;
  text-align: center;
  text-decoration: none;
  border-radius: 0.2em;
}
.product-navigation a.active {
  font-weight: normal;
  background-color: hsla(152, 65%, 80%, 1);
}
.products {
  display: flex;
  flex-wrap: wrap;
}
.products figure,
.products img {
  width: 100%;
  margin: 0;
}
.products a {
  color: inherit;
}
.products .product {
  display: block;
  width: 10em;
  margin: 1em;
}
.product button {
  width: 100%;
}
</style>
