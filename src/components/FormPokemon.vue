<template>
  <b-container fluid="md" center>
    <b-form-input
      class="searchPkm"
      @keyup.enter="addCard(pkm)"
      v-model="pkm"
      placeholder="Qual pokemon?"
    ></b-form-input>
    <br />
    <br />
    <b-button
      pill
      style="margin-right: 2%;"
      size="md"
      @click="addCard(pkm)"
      variant="primary"
      ><b-icon icon="plus" font-scale="2"></b-icon
    ></b-button>
    <b-button size="md" pill style="margin-right: 2%;" variant="success"
      >Calcular Estatística</b-button
    >
    <b-button
      pill
      style="margin-right: 2%;"
      size="sm"
      @click="cleanPkm()"
      variant="light"
      ><b-icon icon="arrow-clockwise" animation="spin" font-scale="2"></b-icon
    ></b-button>
    <br />
    <br />
    <b-card-group column id="card_deck">
      <div v-for="(pkm, index) in arrayPkm" :key="index">
        <b-row >
          <Card
            :num="pkm.id"
            :tittle="pkm.pokemon"
            :hp ="pkm.content.status.hp"
            :atak ="pkm.content.status.atak"
            :def ="pkm.content.status.def"
            :satak ="pkm.content.status.satak"
            :sdef ="pkm.content.status.sdef"
            :speed ="pkm.content.status.speed"
            :img_url="pkm.img"
            content="Hello!"
          />
        </b-row>
        <b-button style="margin-bottom: 21px;" size="sm" pill @click="removeCard(pkm.id)" variant="danger"
          ><b-icon icon="x-circle" font-scale="1"></b-icon
        ></b-button>
      </div>
    </b-card-group>
  </b-container>
</template>

<script>
import Card from "@/components/Card.vue";
import axios from "axios";

export default {
  name: "FormPokemon",
  data() {
    return {
      cards: 0,
      arrayPkm: [],
      TeamFull: false,
      pkm: "",
    };
  },
  components: {
    Card,
  },
  methods: {
    addCard() {
      if (
        this.pkm != "" &&
        this.arrayPkm.some((pkm) => pkm.pokemon === this.pkm) != true
      ) {
        if (this.arrayPkm.length <= 5) {
          // Axios

          const url = `https://pokeapi.co/api/v2/pokemon/${this.pkm}`;

          axios
            .get(url)
            .then((response) => {
              let result = {
                id: response.data.id,
                pokemon: response.data.name,
                img: response.data.sprites.front_default,
                content: {
                  status: {
                    hp: response.data.stats[0].base_stat,
                    atak: response.data.stats[1].base_stat,
                    def : response.data.stats[2].base_stat,
                    satak : response.data.stats[3].base_stat,
                    sdef : response.data.stats[4].base_stat,
                    speed: response.data.stats[5].base_stat
                  },
                  abilities: {},
                  types: {},
                },
              };
              console.log(result.id);
              this.arrayPkm.push(result);
            })
            .catch((error) => {
              console.log(error);
              this.pkm = "";
              alert("Esse pokemon não existe!");
            });

          // End Axios

          console.log(this.arrayPkm);

          this.cards++;

          this.pkm = "";
        } else {
          this.TeamFull = true;

          alert("Seu time já está completo!");
        }
      } else {
        alert("Campo não preenchido ou esse pokemon já faz parte do seu time!");
        this.pkm = "";
      }
    },
    removeCard(id) {
      console.log("Pokemon excluído: ", id);

      this.arrayPkm = this.arrayPkm.filter((pkm) => {
        return pkm.id != id;
      });

      this.cards--;
    },
    cleanPkm() {
      this.arrayPkm = [];
      this.cards = 0;
    },
  },
};
</script>

<style>
.searchPkm {
  width: 50%;
  margin: 0 auto;
  text-align: center;
}

</style>
