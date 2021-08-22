<template>
  <div class="systems">
     <v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        Konfigurator ogrodzeń kost-bet 
      </span>
    </v-card-title>
    <v-select @input="rysuj_mape()" :items="bloczek" item-text="nazwa" item-value="id" v-model ="bloczek_id" label="Bloczek" outlined ></v-select>
    <!-- <v-text-field type="number" outlined single-line step="1" v-model="dl_og"></v-text-field> -->
     </v-card>
          <horizontal-scroll>
          <div @mouseleave="draw_type = 0" v-bind:style="{width:szerokosc_mapy + 'px'}" class="mapa">
          <div @mousedown="draw_type = 1, Rysuj2(n)" @mouseover="Rysuj2(n)" @mouseup="draw_type = 0" :style="{height:height +'px' ,width:width + 'px'}" v-for="(v,n) in map" :key="n" :class='map[n].cla' class = "frame unselectable" ></div>
          <!-- {{map[n].id}} -->
          </div>
         </horizontal-scroll>


  <!-- <table>
    <th v-for="(v,k) in tableData" :key="k">
       <tr @click="editReply(k)" v-bind:style="{ 'background-color': tableData[k].type}">
       <td>{{v.type}}</td>
       </tr>
    </th>
  </table> -->
<div class="control-panel">
<v-btn @click ="selected_draw = 1" class="btn" color="primary">bloczek</v-btn>
<v-btn @click ="selected_draw = 2" class="btn" color="green">Wypełnienie</v-btn>
<v-btn @click ="selected_draw = 3" class="btn" color="orange">Czyszczenie</v-btn>
</div>


<div class="cena" color="primary">Ilość bloczków: {{ilosc_bloczkow}}</div>
<div class="cena" color="primary">Powierzchnia pól ogrodzeniowych: {{ilosc_paneli*0.075}} m2</div>


     <!-- </v-card> -->
  </div>



</template>


<script>

import HorizontalScroll from 'vue-horizontal-scroll'
import 'vue-horizontal-scroll/dist/vue-horizontal-scroll.css'
export default {

    components: {
        HorizontalScroll
    },


data: () => ({

bloczek:[
  // {id:0, nazwa:'Brak', waga:0, cena:0, szerokosc:0, wysokosc:0, glebokosc:0, style:'none' },
  {id:0, nazwa:'Kost-Bet Royal Slim 7016', waga:12, cena:45, szerokosc:60, wysokosc:12.5, glebokosc:20, cla:"royalslim" },
  // {id:2, nazwa:'Inny bloczek', waga:12, cena:45, szerokosc:40, wysokosc:40, glebokosc:20, bg:'#0D0D0D' }
],

 tableData:[
   {id:1, type:"yellow"},{id:2, type:0},{id:3, type:2},
 ],
      colorData:{
      "one":"blue",
      "two":"green",
      "three":"red",
     },
map:[{id:0,bg:'none',cla:'none'}],
showMobileMenu: false,
color:'yellow',
fontSize: 30,
width:0,
height:0,
dl_og:20,
dl_siatki:0,
szerokosc_mapy:0,
i:0,
bloczek_id:0,
map_visible:false,
draw_type:0,
selected_draw:1,
ilosc_bloczkow:0,
ilosc_paneli:0,

rysuj_mape(){
  this.width = this.bloczek[this.bloczek_id].szerokosc*1.5;
  this.height = this.bloczek[this.bloczek_id].wysokosc*1.5;
  this.dl_siatki = Math.round((this.dl_og*100) / this.bloczek[this.bloczek_id].szerokosc);
  this.szerokosc_mapy = (this.dl_siatki*this.bloczek[this.bloczek_id].szerokosc*2)+this.dl_siatki;

// if(this.map_visible == false){
for (let i = 1; i < this.dl_siatki*(400/this.bloczek[this.bloczek_id].wysokosc) ; i++){
    this.map.push({id:i,bg:'none',cla:'none'});
    }
    this.map_visible = true;
// }

},

Rysuj2(index){

if(this.draw_type == 1 && this.selected_draw == 1 && (this.map[index].cla != this.bloczek[this.bloczek_id].cla)){
    if(this.map[index].cla == 'palisada'){this.ilosc_paneli -=1}
    this.map[index].cla = this.bloczek[this.bloczek_id].cla;
    this.ilosc_bloczkow += 1;

}
if(this.draw_type == 1 && this.selected_draw == 2 && (this.map[index].cla != 'palisada')){
    if(this.map[index].cla == 'royalslim'){this.ilosc_bloczkow -=1}
    this.map[index].cla = 'palisada'
    this.ilosc_paneli += 1;
}

if(this.draw_type == 1 && this.selected_draw == 3){
// this.map[index].cla = 'none';
// this.ilosc_paneli -= 1;

if(this.map[index].cla == 'palisada'){
  this.map[index].cla = 'none';
  this.ilosc_paneli -=1;
  }
if(this.map[index].cla == 'royalslim')
{
  this.map[index].cla = 'none';
  this.ilosc_bloczkow -=1;
  }
}

},

}),

// beforeMount:{
//   rysuj_mape(){
//     for (let i = 1; i < (this.dl_siatki*20)+1 ; i++){
//     this.map[i]= 0;
//   }
//   }
// },
// beforeMount(){

// console.log("before");
// // for (let i = 1; i < 5000 ; i++){
// //     this.map[i]= 0;
// //   }

// for (let i = 0; i < 100 ; i++){
//     this.map.push({id:'6',style:'green'});
//     }
// console.log(this.map);
// },



methods:{

editReply(index) {
      console.log(index)
      if(index == 1){console.log("kliknąłeś w dwójkę bo index jeden to drugi numer")
      this.tableData[index].type = "black";
      }
    }

}
}
</script>

<style lang="scss">

.mapa {
// max-height: 500px;
background-color:#260B0B;
display:flex;
flex-wrap: wrap;
width:5000px;
background-image: url(../assets/house2.jpg);
background-size: contain;
}

.red{
  background: color #36454f;
}

.palisada
{
background-image: url(../assets/palisada.png);
border:none;
}

.active{
  background-color:red;
}

.unselectable {
  user-select: none;
  user-drag:none;
  -moz-user-select: none;
  -webkit-user-drag: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}

.royalslim
{
  background-color: #383e42;
}

.frame
{
// border: 1px dotted rgba(0, 0, 0, .2);
// padding:1px;
}

.frame:hover{
opacity:0.6;
background-color: #bbbbbb;
border: 2px solid rgba(0, 0, 0, 1);
cursor:pointer;
}

div .control-panel{
margin:10px;
}

.btn
{
margin:0px 5px;
width:200px;
background-color:red;
}

div .calcsection{

margin-bottom:0px;
}
</style>