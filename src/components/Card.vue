<template>
  <div>
  <b-card
    :title= tittle
    :num = num
    :img-src= img_url
    img-alt="Image"
    tag="article"
    style="max-width: 20rem;"
    class="mb-4 myCard"
  >
    <b-card-text>
      {{content}}
    </b-card-text>
  </b-card>

</div>
</template>

<script>
export default {
  name: "Card",
  props: {
    tittle: String,
    content: String,
    num: Number,
    img_url : String
  },
};
</script>

<style>

.myCard {
  width: 1500px;
  
}


</style>
