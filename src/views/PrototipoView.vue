<template>
    <div class="prototipo">
        <b-navbar class="b-navbar-dark" type="dark" variant="info">
            <b-navbar-brand>Nome azienda</b-navbar-brand>
        </b-navbar>

        <br>
        <b-img
            src="/images/bottiglia.png"
            alt="bottiglia"
            fluid
            thumbnail
        ></b-img>

        <p class="text-center, font-weight-bold">{{ nomeVino }}</p>

        <p class="text-center">Origine: {{produzione}} ● {{tipologia}} ● {{alcohol}} ● {{ quantita }}</p>

        <b-navbar class="b-navbar-dark" type="dark" variant="info">
            <b-navbar-brand>Dichiarazione nutrizionale</b-navbar-brand>
        </b-navbar>

        <br>
        <b-table :items="valoriNutritivi">
            <template #head(first_col)>
                <p>Elementi nutritivi</p>
            </template>
            <template #cell(first_col)="data">
                <p class="text-left" v-html="data.value"></p>
            </template>
            <template #head(second_col)>
                <p>Quantità per 100 ml</p>
            </template>
            <template #cell(second_col)="data">
                <p class="text-right" v-html="data.value"></p>
            </template>
        </b-table>

        <b-navbar class="b-navbar-dark" type="dark" variant="info">
            <b-navbar-brand>Ingredienti</b-navbar-brand>
        </b-navbar>

        <br>
        <p class="text-left">{{ ingredienti }}</p>

        <b-navbar class="b-navbar-dark" type="dark" variant="info">
            <b-navbar-brand>Etichetta ambientale</b-navbar-brand>
        </b-navbar>

        <br>
        <b-table thead-class="d-none" :items="ambiente">
            <template #cell(icon)="data">
                <b-img
                    v-if='data.value == "bottiglia"'
                    src="/images/bottiglia-s.png"
                    alt="bottiglia"
                    fluid
                    thumbnail
                ></b-img>
                <b-img
                    v-if='data.value == "capsula"'
                    src="/images/capsula-s.png"
                    alt="bottiglia"
                    fluid
                    thumbnail
                ></b-img>
                <b-img
                    v-if='data.value == "tappo"'
                    src="/images/tappo-s.png"
                    alt="bottiglia"
                    fluid
                    thumbnail
                ></b-img>
            </template>
            <template #cell(text)="data">
                <p class="text-left" v-html="data.value"></p>
            </template>
        </b-table>
        <p class="text-center">Verifica le disposizioni del tuo Comune</p>

    </div>
</template>

<script>
export default {
  name: 'PrototipoView',
  data() {
      return {
        nomeVino: "Vino ABC",
        produzione: "Italia",
        tipologia: "Vino rosso",
        alcohol: "10% vol",
        quantita: "750 ml",
        ingredienti: "Acqua, farina, lievito, burro",
        valoriNutritivi: [
          //{ first_col: 'Elementi nutritivi', second_col: 'Quantità per 100 ml' },
          { first_col: 'Grassi<br>di cui:<br>- acidi grassi saturi', second_col: '0 g<br><br>0 g' },
          { first_col: 'Carboidrati<br>di cui:<br>- zuccheri', second_col: '0,8 g<br><br>0,8 g' },
          { first_col: 'Proteine', second_col: '0 g' },
          { first_col: 'Sale', second_col: '0,03 g' }
        ],
        ambiente: [
          { icon: 'bottiglia', text: '<b>Bottiglia</b><br>Raccolta vetro<br><b>GL 73</b>' },
          { icon: 'tappo', text: '<b>Tappo</b><br>Raccolta differenziata dedicata o raccolta differenziata per rifiuti organici<br><b>FOR 51</b>' },
          { icon: 'capsula', text: '<b>Capsula</b><br>Raccolta alluminio<br><b>C/ALU 90</b>' },
        ]
      }
    }
}
</script>

<style scoped>
.b-navbar-dark {
  background-color: rgb(158, 37, 72) !important;
  color: white;  /* colore del testo */
}
</style>