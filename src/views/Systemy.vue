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
        <v-btn class="ma-2 btn" color="indigo" dark @click ="selected_draw = 1"><v-icon  medium color="white">mdi-help</v-icon>Pomoc</v-btn>
         <v-btn @click ="clear_map()" class="ma-2" right dark color="red"><v-icon  medium color="white">mdi-autorenew</v-icon>Resetuj</v-btn>
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

</div>
     </v-card>
          <horizontal-scroll>
          <div @mouseleave="draw_type = 0" v-bind:style="{width:szerokosc_mapy + 'px'}" class="mapa">
          <div @mousedown="draw_type = 1, Rysuj2(n)" @mouseover="Rysuj2(n)" @mouseup="draw_type = 0" :style="{height:height +'px' ,width:width + 'px'}" v-for="(v,n) in map" :key="n" :class='map[n].cla' class = "frame unselectable" ><span class="legend" v-if="n<44 && n>0">{{n*60}}</span><span class="legend" v-if="n>43 && n%44==0">{{(1012-n)/44*12.5}}</span><span class="legend" v-if="n==0">{{"Centymetry"}}</span></div>
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
<h3 color="primary" class="display-2 ml-10 mt-4 font-weight-light">Do wyboru do koloru:</h3>
<div class="colors">
<div class="color">1</div>
<div class="color">1</div>
<div class="color">1</div>
<div class="color">1</div>
<div class="color">1</div>
<div class="color">1</div>
</div>

             </v-col>
             <v-col cols="6">
<!-- <h1 class="display-4 mt-14">Wyjątkowe</h1> -->
<h2 color="primary" class="display-1 mt-16 font-weight-light">Ogrodzenie na lata</h2>
<h3>Ogrodzenie murowane budujesz raz na kilkadziesiąt lat, co w porównaniu z trwałością innych ogrodzeń wychodzi najkorzystniej.</h3>

             <h2 color="primary" class="display-1 mt-16 font-weight-light">Nowoczesny design</h2>
<h3>Idealnie prosty kształt będzie zawsze nowoczesny. Budując ogrodzenie bez dodatkowych elementów deroracyjnych możesz być pewien, że nigdy nie wyjdzie z mody.</h3>

             <h2 color="primary" class="display-1 mt-16 font-weight-light">Możliwość kombinacji</h2>
<h3>Palisa stalowa, nierdzewna lub aluminiowa? a może system ogrodzeń Budmat lub SMW? Royal Slim pasuje każdy rodzaj przęseł</h3>

             </v-col>
           </v-row>
         </v-parallax>
<v-expansion-panels>


         <v-expansion-panel
    >
      <v-expansion-panel-header>Instrukcja montażu</v-expansion-panel-header>
      <v-expansion-panel-content>
         <div class="systems pa-8">
    <h1>Instrukcja montażu</h1>
    <h3>1.</h3>

<p>Prace rozpoczynamy od wykonania fundamentu pod ogrodzenie. Wykop fundamentowy
wykonujemy na głębokość poniżej strefy przemarzania (90cm-150cm), biorąc pod uwagę
rozmieszczenie słupków. Ławy fundamentowe zbroimy poziomo drutem żebrowanym 4 *fi 12
strzemiona wykonujemy z drutu fi 6, stosujemy również zbrojenie pionowe pod rozmieszczone
słupki 4*fi12. Przygotowanyi zazbrojonywykop zalewamy betonem klasy C20/25. Ewntualne
niewielkie ubytki i nierówności powstałe w płaszczyźnie fundamentu uzupełniamy zaprawą
wyrównującą. Na tak przygotowaną ławę fundamentową rozkładamy folię izolacji poziomej
chroniącą przed przesiąkaniem wilgoci z gruntu.</p>
<h3>2.</h3>
<p>Przed rozpoczęciem montażu elementy murowe powinny zostać oczyszczone z luźnych
pozostałości produkcyjnych. Montaż ogrodzenia łupanego w zestawie S38+P22
rozpoczynamy od elementów słupkowych typu„S",a następnie powstałą przestrzeń między
nimi wypełniamy elementami typu„P". Montaż ogrodzenia łupanego w zestawie S22+P22 oraz
S38+P38 rozpoczynamy od elementów podmurówkowych, a następnie montujemy na nich
elelmenty słupkowe. Do łączenia pustaków łupanych typu „P" i „S" używamy specjalistycznych
mrozoodpornych zapraw klejowych lub klejo-uszczelniaczy. Ważne aby łączenie
montowanych ze sobą elementów było wykonane ze szczególną starannością i dokładnością
uniemożliwiając w późniejszym czasie wypłynięcie betonu, a co za tym idzie zacieku lub
wykwitu na wierzchniej warstwie ogrodzenia. Na tym etapie montujemy również zawiasy do
furtek i bram oraz mocowania do przęseł. Do poziomowania i niwelacji powstałych odchyleń
możemy używać klinikow glazurniczych. Wymurowane elementy zalewamy oraz zagęszczamy
mieszanką betonową wodoszczelną klasy C30/37 na bazie piasków i żwirów płukanych oraz
cementu klasy CM i bez dodatków popiołowych. W razie wypłynięcia mieszanki betonowej na
lico ogrodzenia należy niewłocznie usunąć zabrudzenie spłukającje obficie wodą. Ważne aby
przed zamontowaniem daszków po każdym zakończonym dniu pracy zabezpieczyć słupki oraz
podmurówkę przed działaniem warunków atmosferycznych.</p>
<h3>3.</h3>

<p>Po wymurowaniu słupków i podmurówek oraz zalaniu ich betonem możemy przystąpić do
montażu daszków. Daszki kleimy używając zaprawy klejowej, a połączenie między daszkami
i między daszkami a pustakami uszczelniamy silikonem.</p>

<h3>4.</h3>
<p>Po zakończeniu okresu dojrzewania betonu zalecamy impregnację całego ogrodzenia,
a następnie montaż bram, furtek oraz przęseł.</p>

  </div>
      </v-expansion-panel-content>
    </v-expansion-panel>

</v-expansion-panels>

    <v-card>
           <v-row>
             <v-col>
<h1 class="display-4 ml-10 mt-14">Fundamenty</h1>
<h3 color="primary" class="display-2 ml-10 mt-4 font-weight-light">Systemowo</h3>
<h3 class="ml-10 mt-6">Możesz wykopać oraz odlać fundamenty tradycyjnie do strefy przemarzania bądź skorzystać z nowoczesnego systemu. Szczegóły znajdziesz w instrukcji montażu.</h3>

             <v-img class="mt-6" contain height="400" src="../assets/fundamenty.jpg"></v-img>
             <h3 class="ml-10 mt-6">Zaplanowane ogrodzenie ma długość X mb. Podaj ilość słupów składających się z minimum 4 bloczków jeden na drugim</h3>
             <h3 class="ml-10 mt-6">Długość ogrodzenia:</h3>
             <h3 class="ml-10 mt-6">Ilość słupów:</h3>
             <h3 class="ml-10 mt-6">Ilość belek:</h3>
             <h3 class="ml-10 mt-6">Szacunkowy koszt:</h3>
             </v-col>
             <v-col>
<div class="s1img"><v-img src="../assets/lupany16-schemat.jpg"></v-img></div>
             </v-col>
           </v-row>
           <v-row>
<v-col>
<h3 color="primary" class="display-2 ml-10 mt-4 font-weight-light">Tradycyjnie </h3>
<h3 class="ml-10 mt-6">Zaplanowane ogrodzenie ma długość X mb. Podaj wymiary aby obliczyć ilość potrzebnego betonu.Tradycyjny fundament zakłada 30cm x 80 cm x długość</h3>
<h3 class="ml-10 mt-6">Długość ogrodzenia</h3>
<h3 class="ml-10 mt-6">Szerokość</h3>
<h3 class="ml-10 mt-6">Głębokośc (poniżej strefy przemarzania)</h3>
<h3 class="ml-10 mt-6">Cena betonu za m2</h3>
<h3 class="ml-10 mt-6">Szacunkowy koszt:</h3>

</v-col>
<v-col><v-img class="mt-6" contain height="400" src="../assets/cos.jpg"></v-img></v-col>

           </v-row>
         </v-card>

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
legend:true,
lop:0.5,

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

legenda(){
this.legend = !this.legend
if(this.legend == true) {this.lop = 1}else {this.lop = 0.5}
// for (let i = 1; i < this.dl_siatki*(400/this.bloczek[this.bloczek_id].wysokosc) ; i+44){
this.map[0].cla = 'legend'
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
},


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
  border:rgb(53, 53, 53) 1px solid;
}

.legend
{
display:block;
text-align: center;
justify-content: center;
vertical-align: top;
margin:0,auto;
}

.frame{
  display:flex;
  align-items: left;
  justify-content: left;
  font-size: 15px;
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