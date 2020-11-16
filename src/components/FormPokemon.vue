<template>
  <div>
    <b-container fluid="md" center>
      <b-form-input
        class="searchPkm"
        v-model="pkm"
        placeholder="Qual pokemon?"
      ></b-form-input>
      <br />
      <b-button @click="addCard()" variant="primary"
        >Add Pokemon</b-button
      >
      <br />
      <br />
      <b-card-group deck id="card_deck">
        <div v-for="card in cards" :key="card">
          <b-row align-h="center">
            <Card class='myCard' />
          </b-row>
        </div>
      </b-card-group>
    </b-container>
  </div>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  name: "FormPokemon",
  data() {
    return {
      cards: 0,
      TeamFull: false,
      pkm: "",
    };
  },
  components: {
    Card,
  },
  methods: {
    addCard() {
      this.cards++;
      if (this.cards <= 6) {
        console.log("Add Pkm");
      } else {
        this.TeamFull = true;
        alert("Time Completo");
      }
    },
  },
};
</script>

<style>
.searchPkm {
  height: 30px;
  width: 480px;
  margin: 0 auto;
  text-align: center;
}
#card_deck{
  display: flex;
  align-items: center;
  justify-content: center;
}

</style>
