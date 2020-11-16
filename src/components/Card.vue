<template>
  <div>
  <b-card
    :title= tittle
    img-src="https://imgix.bustle.com/uploads/image/2020/2/13/da1a1ca4-95ec-40ea-83c1-4f07fac8b9b7-eqb9xdwx0auhotc.jpg"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-4"
  >
    <b-card-text>
      {{content}}
    </b-card-text>

    <b-button href="#" variant="primary">{{detail_item}}</b-button>
  </b-card>
</div>
</template>

<script>
export default {
  name: "Card",
  props: {
    tittle: String,
    content: String,
    detail_item: String
  },
};
</script>

<style></style>
