<template>
<v-container>
  <v-card>
     <v-card-title>Grafika</v-card-title>
  </v-card>



    <v-row>
    <v-col>
    <v-card
    class="mx-auto text-center chart"
    color="blue"
    dark
  >
    <v-card-text>
      <v-sheet color="rgba(0, 0, 0, .12)">
        <v-sparkline
          :value="value"
          color="rgba(255, 255, 255, .7)"
          height="100"
          padding="24"
          stroke-linecap="round"
          smooth
        >
          <template v-slot:label="item">
            PLN {{ item.value }}
          </template>
        </v-sparkline>
      </v-sheet>
    </v-card-text>

    <v-card-text>
      <div class="text-h4 font-weight-thin">
        Cena netto prętów zrojeniowych na przestrzeni ostatnich miesięcy
      </div>
    </v-card-text>
  </v-card></v-col>
    <v-col>
      <v-card
       class="mx-auto text-center">
    <v-card-title>DODAJ PRODUKT DO WYCENY</v-card-title>
    <div class="fields">
          <v-select
            :items="produkty"
            item-value="id"
            item-text="nazwa"
            clearable
            flat
            solo-inverted
            hide-details
            label="Produkt"
            v-model="produkt"
          ></v-select>
            <v-spacer></v-spacer>
            <v-select
              flat
              solo-inverted
              hide-details
              :items="jednostka"
              label="Jednostka"
              v-model="jednostkamiary"
            ></v-select>
            <v-spacer></v-spacer>
            <v-text-field
              type="number"
              flat
              solo-inverted
              hide-details
              :items="keys"
              label="Ilość"
              v-model="ilosc"
            ></v-text-field>
            </div>
       <v-card-actions class="justify-center">
      <v-btn
        block
        text
        color="blue"
        @click="dodawaj()"
      >
        Dodaj
      </v-btn>
    </v-card-actions>
     </v-card></v-col>
    </v-row>
     <br>

        <br>
     <v-card>
       <v-card-title>POZYCJE</v-card-title>
       <div class="poz" v-for="(v,n) in pricedata" :key="n">{{pricedata[n].nazwa}} {{pricedata[n].jm}} {{pricedata[n].il}}</div>
     </v-card>
<br>
     <v-card>
       <v-card-title>ZAMÓWIENIE</v-card-title>
     </v-card>
</v-container>
</template>

<script>
export default {

    data: () => ({

 price_table: [
          {id:0,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:1,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:2,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:3,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:4,ilosc: 0,c_j: 0,c_n:0,c_b:0},
        ],

        produkty: [
          {id:0,nazwa:"Pręt zebrowany FI 6", waga:0.6},
          {id:1,nazwa:"Pręt zebrowany FI 8", waga:0.8},
          {id:2,nazwa:"Pręt zebrowany FI 10", waga:1},
          {id:3,nazwa:"Pręt zebrowany FI 12", waga:1.2},
          {id:4,nazwa:"Pręt zebrowany FI 14", waga:1.4},
        ],

        jednostka: [
          "Kilogram",
          "Metr",
          "Tona",
        ],

        pricedata:[
          {nazwa:'pręt zebrowany fi 6',jm:3,il:45},
          {nazwa:'pręt zebrowany fi 8',jm:2,il:134},
        ],

        produkt:0,
        jednostkamiary:0,
        ilosc:0,

        pricelicznik:1,

        value: [
        3223,
        3446,
        3775,
        3810,
        3190,
        4210,
        4360,
      ],
      month:[
        "styczen",
        "luty",
      ],

        elo:2,

        dodawaj()
        {
          this.pricedata.push({nazwa:this.produkty[this.produkt].nazwa,jm:this.jednostkamiary,il:this.ilosc})
        }


    })

}
</script>

<style>

.fields{
  display:flex;
  padding:20px 20px;
}
.container{
  max-width:100%;
  width:100%;
}
.chart{
  width:100%;
}

</style>