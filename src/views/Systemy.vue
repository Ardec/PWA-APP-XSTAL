<template>
  <div class="systems">
      
     <v-card class="calcsection color-gr2">
       <h3 pcolor="primary" class="display-2 mt-4 ml-4 font-weight-light">Planer Ogrodzenia KOST-BET Royal Slim</h3>
       <v-card-title class="text-center justify-center py-6">
    </v-card-title>
        <div class="control-panel">
        <v-btn class="ma-2 btn" color="indigo" dark @click ="selected_draw = 1"><v-icon  medium color="white">mdi-shape-rectangle-plus</v-icon>Bloczek</v-btn>
        <v-btn @click ="selected_draw = 2" class="ma-2 btn" dark color="black"><v-icon  medium color="white">mdi-menu</v-icon>Palisada</v-btn>
        <v-btn @click ="selected_draw = 3" class="ma-2 btn" dark color="purple"><v-icon  medium color="white">mdi-delete-forever-outline</v-icon>Usuń </v-btn>
        <div class="cena" color="primary"></div>
        <v-textarea
          label="ILOŚĆ BLOCZKÓW ( SZT )"
          outlined
          rows="1"
          disabled
          v-model="ilosc_bloczkow"
        >
        </v-textarea>

        <v-textarea
          label="POWIERZCHNIA PALISADY ( M2 )"
          outlined
          rows="1"
          disabled
          v-model="ilosc_paneli"
        ></v-textarea>

         <v-btn @click ="clear_map()" class="ma-2" right dark color="red"><v-icon  medium color="white">mdi-autorenew</v-icon>Zacznij od nowa</v-btn>

</div>
     </v-card>
          <horizontal-scroll>
          <div @mouseleave="draw_type = 0" v-bind:style="{width:szerokosc_mapy + 'px'}" class="mapa">
          <div @mousedown="draw_type = 1, Rysuj2(n)" @mouseover="Rysuj2(n)" @mouseup="draw_type = 0" :style="{height:height +'px' ,width:width + 'px'}" v-for="(v,n) in map" :key="n" :class='map[n].cla' class = "frame unselectable" ></div>
          </div>
         </horizontal-scroll>

         <v-card>
           <v-row>
             <v-col>
<h1 class="display-4 ml-10 mt-4">Royal Slim</h1>
<h3 pcolor="primary" class="display-2 ml-10 mt-4 font-weight-light">Idealny wymiar</h3>
             </v-col>
             <v-col>
<div class="s1img"><v-img src="../assets/slim.jpg"></v-img></div>
             </v-col>
           </v-row>
         </v-card>

         <v-parallax height="600" src="../assets/dworskalewa.jpg">
         <v-row>
             <v-col>

             </v-col>
             <v-col cols="6">
<!-- <h1 class="display-4 mt-14">Wyjątkowe</h1> -->
<h2 color="primary" class="display-1 mt-16 font-weight-light">Wyjątkowe projekty</h2>
<h3>Lorem ipsum dolor sit amet consectetur adipisicing elit. Porro incidunt fugit delectus, nulla soluta ducimus quae facere praesentium, illo consequatur dicta a quis, at pariatur blanditiis totam unde ex quo?</h3>
             </v-col>
           </v-row>
         </v-parallax>

         <!-- <v-card>

           <v-row>
             <v-col>1

               dasadsasd

               dasadsasda

               <h1>asdasd</h1>
             </v-col>
             <v-col>2</v-col>
           </v-row>
         </v-card> -->

<v-bottom-navigation height="64px" v-model="value" fixed="true">
      <div class="iconsfooter"><v-icon color="blue" class="footericon">mdi-cash-multiple</v-icon><span class="pricetext">{{Math.round(suma_pln*1.23)}} PLN</span></div>
  </v-bottom-navigation>



  </div>



</template>


<script>

import HorizontalScroll from 'vue-horizontal-scroll'
import 'vue-horizontal-scroll/dist/vue-horizontal-scroll.css'
export default {

    components: {
        HorizontalScroll
    },

    mounted(){
    this.rysuj_mape()
  },


data: () => ({

bloczek:[
  {id:0, nazwa:'Kost-Bet Royal Slim 7016', waga:12, cena:45, szerokosc:60, wysokosc:12.5, glebokosc:20, cla:"royalslim" },
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
suma_pln:0,
map_visible:false,
draw_type:1,
selected_draw:0,
ilosc_bloczkow:0,
ilosc_paneli:0,
cenapalisada:800,
palisadam2:0,

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

clear_map(){

for (let i = 1; i < this.dl_siatki*(400/this.bloczek[this.bloczek_id].wysokosc) ; i++){
    this.map[i].bg="none"
    this.map[i].cla="none"
    this.ilosc_bloczkow=0
    this.ilosc_paneli=0
}

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

this.suma_pln = this.ilosc_bloczkow* 45

},

}),


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
display:flex;
flex-wrap: wrap;
background-image: url(../assets/houselong.jpg);
background-size: cover;
}

.block{
  display:block;
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
display:flex;
flex-grow: 1;
flex-wrap: wrap;
justify-content: center;
}

.btn
{
width:140px;
background-color:red;
}

div .calcsection{

margin-bottom:0px;
}
</style>