<template>
  <div>
  <b-card
    :title= tittle
    :num = num
    :img-src= img_url
    :hp = hp
    :atk = atak
    :def = def
    :satak = satak
    :sdef = sdef
    :speed = speed
    img-alt="Image"
    tag="article"
    style="max-width: 20rem;"
    class="mb-4 myCard"
  >
    <b-card-text>
      {{content}}
      <br>
      Hp: {{hp}}
      <br>
      Atak: {{atak}}
      <br>
      Def: {{def}}
      <br>
      S.Atak : {{satak}}
      <br>
      S.Def : {{sdef}}
      <br>
      Speed : {{speed}}
      
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
    img_url : String,
    hp: Number,
    atak : Number,
    def : Number,
    satak : Number,
    sdef : Number,
    speed : Number
  },
};
</script>

<style>

.myCard {
  width: 1000px;
  margin-right: 65px;
  
  left: 28px;
}


</style>
