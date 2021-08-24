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
<v-row>1</v-row>
<v-row>2</v-row>
<v-row>3</v-row>

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
    <h1>Regulamin montażu ogrodzeń panelowych</h1>
    <br>

<h3>Przed rozpoczęciem prac inwestor jest zobowiązany do: </h3>

<ul>Udostępnienia posesji oraz mediów lub dopłaty zgodnie z cennikiem.</ul>

<ul>Wyznaczenia słupków granicznych ogrodzenia na każdym załamaniu.</ul>
<ul>Wyznaczenia umiejscowienia bramy oraz furtki. </ul>
<ul>Wyznaczenia umiejscowienia bramy oraz furtki. </ul>
<ul>Wysprzątania i przygotowania terenu pod budowę (koszenie itd.)</ul>
<ul>Wykonawca buduje ogrodzenie w miejscu wskazanym przez inwestora i nie ponosi odpowiedzialności za nieprawidłowe wskazanie biegu granic.</ul>
<ul>Ustalenia uskoków ogrodzenia</ul>

<br>

<h3>Wycena nie obejmuje:</h3>
<ul>prac ziemnych</ul>
<ul>niwelacji terenu</ul>
<ul>koszenia</ul>
<ul>sprzątania ( wszelkie pozostałości - kamienie, ziemia, piasek ) zostają na działce inwestora</ul>
<ul>transportu materiałów dodatkowych</ul>
<ul>wykonania instalacji elektrycznych</ul>
<ul>rozbiórki, układania kostki brukowej oraz modyfikacji innej infrastruktury</ul>
<ul>demontażu</ul>
<ul>wycinania paneli w miejscach skrzynek, przyłączeń lub przeszkód</ul>
<ul>prowadzenia instalacji elektrycznej do bramy przesuwnej</ul>
<ul>betonu powyżej poziomu gruntu ( podnoszenia ogrodzenia )</ul>
<ul>montażu elementów z powierzonego materiału.</ul>
<ul>Materiału dodatkowego, np. dłuższych słupków, wymiany lub dodatkowych podmurówek,</ul>
<ul>Montażu i materiału na słupy krańcowe ogrodzenia panelowego. Pole panelowe składa się z zawsze z jednego słupka i jednego pola, a każde następne jest dołączone do poprzednich.</ul>

<br>

<h4>Uzupełnianie ziemi na różnicach wysokości leży po stronie inwestora.</h4>
<h4>Pola docinane liczą się jako pełne ( 2.6mb x cena za mb )</h4>
<h4>Termin realizacji może ulec zmianę z uwagi na czynniki zewnętrzne.</h4>

<br>

<p>Wizja w terenie jest płatna 300 zł i zostaje odliczona od końcowej kwoty należności za ogrodzenie. <br>
Po wpłacie zadatku dokonywany jest pomiar na miejscu budowy.W przypadku ostatecznej decyzji podjęcia współpracy, pomiar jest bezpłatny.Wpłata zadatku jest równocześnie rezerwacją ceny materiału.</p>

<p>Zmiany w ofercie są płatne 50 zł / zmiana, muszą zostać zaakceptowane przez obie strony i zgłoszone minimum 24 godziny wcześniej, tak aby nie opóźniały prac.</p>

<p>Oferta cenowa jest ważna przez 14 dni od dnia w którym została do Pani/Pana przekazana.Cena może ulec zmianie jeśli występuje różnica pomiędzy pomiarem a podanymi przez Pana/Panią danymi.</p>

<p>Prosimy o ustalanie prac nie uwzględnionych w ofercie jedynie poprzez biuro.
Prace dodatkowe, nie uwzględnione w umowie są wycenione na 50zł/ netto za godzinę pracy każdego pracownika przebywającego na budowie.</p>

  </div>
      </v-expansion-panel-content>
    </v-expansion-panel>
      
</v-expansion-panels>

    <v-card>
           <v-row>
             <v-col>
<h1 class="display-4 ml-10 mt-14">Fundamenty</h1>
<h3 color="primary" class="display-2 ml-10 mt-4 font-weight-light">Tradycyjnie / Systemowo</h3>
<h3 class="ml-10 mt-6">Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatem soluta necessitatibus cum unde odit culpa mollitia quia? Eveniet sequi quod veniam iure delectus quo assumenda dolorem nihil atque temporibus. Necessitatibus!</h3>
             </v-col>
             <v-col>
<div class="s1img"><v-img src="../assets/lupany16-schemat.jpg"></v-img></div>
             </v-col>
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