<template>
  <v-container>
    <v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        1. KONFIGURATOR OGRODZENIA
      </span>
    </v-card-title>
    <v-row>
<v-col>
  <p class="sitebot">ELEMENTY OGRODZENIA
         <v-tooltip bottom>
      <template v-slot:activator="{ on, attrs }">
        <v-icon
          medium
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          mdi-information-outline
        </v-icon>
      </template>
      <span>
        A. Tylko przy wyborze czarnej stali i ocynkowaniu ogniowym materiał jest zabezpieczony na kilkadziesiąt lat. W innych przypadkach zabezpieczenie jest mniej trwałe na spawach.
        <br>
        B. Profil ramy utrzymuje konstrukcję w pozycji stabilnej i pełni walory estetyczne. Dla lekkich furtek aby obniżyć koszty można zastosować nawet profil 40x40x1.5, dla bram 60x40x2 lub 80x40x2
        <br>
        C. Słupy do furtek i bram przesuwnych to minimum 60x60x2. Do bram dwuskrzydłowych zalecane są 80x80x3.
        <br>
        D. W sprawie szczegółowych informacji technicznych zachęcamy do kontaktu z naszymi doradcami.
      </span>
    </v-tooltip>
         </p>
         <v-select @input="calculate()" :items="panele" item-text="nazwa" item-value="id" v-model ="panel_id" label="Pole" outlined ></v-select>
    <v-select @input="calculate()" :items="podmurowka" item-text="nazwa" item-value="id" v-model ="podmurowka_id" label="Podmurowka" outlined ></v-select>
    <v-select @input="calculate()" :items="laczniki" item-text="nazwa" item-value="id" v-model ="laczniki_id" label="Łączniki" outlined ></v-select>
    <v-select @input="calculate()" :items="slupki" item-text="nazwa" item-value="id" v-model ="slupki_id" label="Słupki" outlined ></v-select>
    <v-slider v-model="dl_og" @input="calculate()" label="Długość ogrodzenia (MB)" step="1" thumb-label="always" min="1" max="300" color="black"></v-slider>
    <v-text-field type="number" outlined single-line step="0.1" v-model="dl_og"></v-text-field>
    <v-checkbox v-on="calculate()" v-model="montaz" label="Wycena ogrodzenia z montażem" color="blue" value="1"></v-checkbox>
</v-col>
<!-- <v-col>
  <p class="sitebot">WIZUALIZACJA poglądowa OGRODZENIA</p>
 <div class="trzyde"> -->
         <!-- <model-stl backgroundAlpha="0" height="300" src="img/fpanel.stl"></model-stl> -->
         <!-- <model-stl v-if="rodzaj_produktu_wybrane_id==0 && selection==1" backgroundAlpha="0" height="300" src="img/fpalisada.stl"></model-stl> -->
    <!-- </div>
</v-col> -->
    </v-row>
    </v-card>


   <v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        2. KOSZTORYS
      </span>
    </v-card-title>
    <v-row>
<v-col>
  <p class="sitebot">Zestawienie materiałów potrzebnych do pokrycia {{dl_og}} mb 
         <v-tooltip bottom>
      <template v-slot:activator="{ on, attrs }">
        <v-icon
          medium
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          mdi-information-outline
        </v-icon>
      </template>
      <span>
        A. Tylko przy wyborze czarnej stali i ocynkowaniu ogniowym materiał jest zabezpieczony na kilkadziesiąt lat. W innych przypadkach zabezpieczenie jest mniej trwałe na spawach.
        <br>
        B. Profil ramy utrzymuje konstrukcję w pozycji stabilnej i pełni walory estetyczne. Dla lekkich furtek aby obniżyć koszty można zastosować nawet profil 40x40x1.5, dla bram 60x40x2 lub 80x40x2
        <br>
        C. Słupy do furtek i bram przesuwnych to minimum 60x60x2. Do bram dwuskrzydłowych zalecane są 80x80x3.
        <br>
        D. W sprawie szczegółowych informacji technicznych zachęcamy do kontaktu z naszymi doradcami.
      </span>
    </v-tooltip>
         </p>
<v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">
            Produkt
          </th>
          <th class="text-left">
            Ilość (szt)
          </th>
          <th class="text-left">
            Cena jedn.
          </th>
           <th class="text-left">
            Cena netto
          </th>
          <th class="text-left">
            Cena brutto
          </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th class="text-left">
            Panel ogrodzeniowy {{panele[panel_id].nazwa}}
          </th>
          <th class="text-left">
            {{price_table[0].ilosc}}
          </th>
          <th class="text-left">
            {{price_table[0].c_j}}
          </th>
           <th class="text-left">
           {{price_table[0].c_n}}
          </th>
          <th class="text-left">
           {{price_table[0].c_b}}
          </th>
        </tr>
        <tr>
          <th class="text-left">
            Podmurówka {{podmurowka[podmurowka_id].nazwa}}
          </th>
          <th class="text-left">
            {{price_table[1].ilosc}}
          </th>
          <th class="text-left">
            {{price_table[1].c_j}}
          </th>
           <th class="text-left">
            {{price_table[1].c_n}}
          </th>
          <th class="text-left">
            {{price_table[1].c_b}}
          </th>
        </tr>
        <tr>
          <th class="text-left">
            {{laczniki[laczniki_id].nazwa}}
          </th>
          <th class="text-left">
            {{price_table[2].ilosc}}
          <th class="text-left">
            {{price_table[2].c_j}}
          </th>
           <th class="text-left">
           {{price_table[2].c_n}}
          </th>
          <th class="text-left">
           {{price_table[2].c_b}}
          </th>
        </tr>
        <tr>
          <th class="text-left">
             {{slupki[slupki_id].nazwa}}
          </th>
          <th class="text-left">
             {{price_table[3].ilosc}}
          </th>
          <th class="text-left">
             {{price_table[3].c_j}}
          </th>
           <th class="text-left">
            {{price_table[3].c_n}}
          </th>
          <th class="text-left">
            {{price_table[3].c_b}}
          </th>
        </tr>

                  <tr v-if="montaz==1">
          <th class="text-left">
             Montaż przęsła
          </th>
          <th class="text-left">
             {{price_table[4].ilosc}}
          </th>
          <th class="text-left">
             {{price_table[4].c_j}}
          </th>
           <th class="text-left">
            {{price_table[4].c_n}}
          </th>
          <th class="text-left">
            {{price_table[4].c_b}}
          </th>
        </tr>

         <tr>
          <th class="text-left">

          </th>
          <th class="text-left">

          </th>
          <th class="text-left">

          </th>
           <th class="text-left">
           Razem brutto:
          </th>
          <th class="text-left">
            {{koszyk}} PLN
          </th>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</v-col>
    </v-row>
    </v-card>

<v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        3. REZERWACJA WYCENY
      </span>
    </v-card-title>
    <v-row>
<v-col>
  <p class="sitebot">ELEMENTY OGRODZENIA
         <v-tooltip bottom>
      <template v-slot:activator="{ on, attrs }">
        <v-icon
          medium
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          mdi-information-outline
        </v-icon>
      </template>
      <span>
        A. Tylko przy wyborze czarnej stali i ocynkowaniu ogniowym materiał jest zabezpieczony na kilkadziesiąt lat. W innych przypadkach zabezpieczenie jest mniej trwałe na spawach.
        <br>
        B. Profil ramy utrzymuje konstrukcję w pozycji stabilnej i pełni walory estetyczne. Dla lekkich furtek aby obniżyć koszty można zastosować nawet profil 40x40x1.5, dla bram 60x40x2 lub 80x40x2
        <br>
        C. Słupy do furtek i bram przesuwnych to minimum 60x60x2. Do bram dwuskrzydłowych zalecane są 80x80x3.
        <br>
        D. W sprawie szczegółowych informacji technicznych zachęcamy do kontaktu z naszymi doradcami.
      </span>
    </v-tooltip>
         </p>
        <v-text-field
            v-model="templateParams.imie"
            :rules="nameRules"
            :counter="20"
            label="Imię"
            required
          ></v-text-field>
          <v-text-field
            v-model="templateParams.nazwisko"
            :rules="nameRules"
            :counter="20"
            label="Nazwisko"
            required
          ></v-text-field>
          <v-text-field
            v-model="templateParams.miejscowosc"
            :rules="nameRules"
            label="Miejscowość"
            required
          ></v-text-field>
          <v-text-field
            v-model="templateParams.ulica"
            :rules="nameRules"
            label="Ulica"
            required
          ></v-text-field><v-text-field
            v-model="templateParams.numer"
            :rules="nameRules"
            :counter="4"
            label="Numer"
            required
          ></v-text-field>
          <v-text-field
            v-model="templateParams.from_name"
            :rules="nameRules"
            label="Adres e-mail"
            required
          ></v-text-field>
          <v-text-field
            v-model="templateParams.phone"
            :rules="nameRules"
            :counter="10"
            label="Numer telefonu"
            required
          ></v-text-field>

          <v-btn @click="wysylaj(templateParams)" block color="primary">Zarezerwuj cenę materiałów</v-btn>
</v-col>
    </v-row>
    </v-card>






<!-- <v-row>
  <v-col>
    1
  <p>Z uwagi na wahania cen materiałów na rynku zalecamy wysłanie informacji do naszego biura. Otrzymają Państwo numer oferty na który można się powołać oraz czasowe zagwarantowanie ceny towaru. Zestawienie materiałów zostanie również wysłane do Państwa.</p>

  </v-col>
  <v-col>
    2
   </v-col>
</v-row> -->



<v-row>
</v-row>
<v-bottom-navigation height="64px" v-model="value" fixed="true">
  <div class="iconsfooter"><v-icon color="blue" class="footericon">mdi-basket-plus-outline</v-icon><span class="pricetext">  {{koszyk}} PLN</span></div>
</v-bottom-navigation>
  </v-container>
</template>

<script>

// import { ModelStl } from 'vue-3d-model';
import emailjs from 'emailjs-com';



  export default {

    // components: { ModelStl },

    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
       templateParams:{
      name: '',
      message:'Regulamin usług montażowych znajduje się na www.modernbau.info, prosimy o zapoznanie się z zasadami',
      to_name:'X - STAL',
      from_name:'',
      imie:'',
      nazwisko:'',
      phone:'',
      miejscowosc: '',
      ulica:'',
      numer:'',
      suma:'',
      transport:'',
      montaz:0,
      cena_montazu:'',
      p1:'',
      p2:'',
      p3:'',
      p4:'',
      p5:'',
      p1przesla:'',
      p2przesla:'',
      p3przesla:'',
      p4przesla:'',
      p5przesla:'',
      p1cj:'',
      p2cj:'',
      p3cj:'',
      p4cj:'',
      p5cj:'',
      p1cn:'',
      p2cn:'',
      p3cn:'',
      p4cn:'',
      p1cb:'',
      p2cb:'',
      p3cb:'',
      p4cb:'',
      p5cb:'',
      dl_og:'',
      },
      panel_id:0,
      montaz:0,
      podmurowka_id:0,
      marza:1.3,
      laczniki_id:0,
      slupki_id:0,
      koszyk: 0,
      dl_og:40,
      przesla:100,
      colors:[
        {id:0,nazwa:'7016',kolor:'#383e42'},
        {id:1,nazwa:'6005',kolor:'#114232'},
        {id:2,nazwa:'9005',kolor:'#0e0e10'},
        {id:3,nazwa:'8017',kolor:'#442f29'},
      ],
       panele: [
          {id:0,nazwa: '3D 1230 fi 4',cena: 47.5,waga: 3,url:'panele'},
          {id:1,nazwa: '3D 1230 fi 5',cena: 70,waga: 5,url:'panele'},
          {id:2,nazwa: 'prosty 1230 6/5/6 ',cena: 68,waga: 5,url:'panele'},
          {id:3,nazwa: 'prosty 1230 8/6/8 ',cena: 68,waga: 5,url:'panele'},
          // {id:4,nazwa: 'Rama Kuźnia TM 1230 - Modernbau',cena: 180,waga: 5,url:'panele'},
          {id:4,nazwa: 'prosty 1430 6/5/6 ',cena: 68,waga: 5,url:'panele'},
          {id:5,nazwa: 'prosty 1430 8/6/8 ',cena: 68,waga: 5,url:'panele'},
          {id:6,nazwa: '3D 1530 fi 4',cena: 57.5,waga: 4,url:'panele'},
          // {id:8,nazwa: 'Rama Kuźnia TM 1530 - Modernbau',cena: 220,waga: 4,url:'panele'},
          {id:7,nazwa: 'prosty 1630 6/5/6 ',cena: 68,waga: 5,url:'panele'},
          {id:8,nazwa: 'prosty 1630 8/6/8 ',cena: 68,waga: 5,url:'panele'},
          {id:9,nazwa: '3D 1530 fi 5',cena: 85,waga: 6,url:'panele'},
          {id:10,nazwa: '3D 1730 fi 4',cena: 66,waga: 6,url:'panele'},
          {id:11,nazwa: '3D 1730 fi 5',cena: 97,waga: 6,url:'panele'},
          {id:12,nazwa: 'prosty 1830 6/5/6 ',cena: 68,waga: 5,url:'panele'},
          {id:13,nazwa: 'prosty 1830 8/6/8 ',cena: 68,waga: 5,url:'panele'},
          {id:14,nazwa: '3D 2030 fi 4',cena: 80,waga: 6,url:'panele'},
          {id:15,nazwa: '3D 2030 fi 5',cena: 116,waga: 6,url:'panele'},
          {id:16,nazwa: 'prosty 2030 6/5/6 ',cena: 68,waga: 5,url:'panele'},
          {id:17,nazwa: 'prosty 2030 8/6/8 ',cena: 68,waga: 5,url:'panele'},
          {id:18,nazwa: 'Brak',cena: 0,waga: 5,url:'panele'},
        ],
        laczniki: [
          {id:0,nazwa: 'Łącznik betonowy 20cm',cena: 6.8,waga: 3,url:'panele'},
          {id:1,nazwa: 'Łącznik metalowy 20cm',cena: 5.5,waga: 3,url:'panele'},
          {id:2,nazwa: 'Łącznik betonowy 30cm',cena: 11.34,waga: 5,url:'panele'},
          {id:3,nazwa: 'Łącznik metalowy 30cm',cena: 6.2,waga: 5,url:'panele'},
          {id:4,nazwa: 'Brak',cena: 0,waga: 5,url:'panele'},
        ],
        podmurowka: [
          {id:0,nazwa: 'Uranos kaseton 2.48 200mm',cena: 27.9,waga: 3,url:'panele'},
          {id:1,nazwa: 'Uranos kaseton 2.48 300mm',cena: 36.46,waga: 3,url:'panele'},
          {id:2,nazwa: 'Uranos pełna 2.48 200mm',cena: 32.98,waga: 3,url:'panele'},
          {id:3,nazwa: 'Uranos pełna 2.48 300mm',cena: 43.6,waga: 3,url:'panele'},
          {id:4,nazwa: 'Uranos pełna 2.516 200mm',cena: 32.98,waga: 3,url:'panele'},
          {id:5,nazwa: 'Uranos pełna 2.516 300mm',cena: 43.6,waga: 3,url:'panele'},
          {id:6,nazwa: 'Brak',cena: 0,waga: 3,url:'panele'},
        ],
        slupki: [
          {id:0,nazwa: 'Słupek ogrodzeniowy 60x40 H-2000',cena: 49,waga: 3,url:'panele'},
          {id:1,nazwa: 'Słupek ogrodzeniowy 60x40 H-2200',cena: 53,waga: 3,url:'panele'},
          {id:2,nazwa: 'Słupek ogrodzeniowy 60x40 H-2300',cena: 56,waga: 3,url:'panele'},
          {id:3,nazwa: 'Słupek ogrodzeniowy 60x40 H-2400',cena: 58,waga: 3,url:'panele'},
          {id:4,nazwa: 'Słupek ogrodzeniowy 60x40 H-2600',cena: 63,waga: 3,url:'panele'},
          {id:5,nazwa: 'Słupek ogrodzeniowy 60x40 H-2800',cena: 68,waga: 3,url:'panele'},
          {id:6,nazwa: 'Słupek ogrodzeniowy 60x40 H-3000',cena: 73,waga: 3,url:'panele'},
          {id:7,nazwa: 'Brak',cena: 0,waga: 3,url:'panele'},
        ],
         slupki_nst: [
          {id:0,nazwa: 'Słupek ogrodzeniowy 60x40 H-2000',cena: 48,waga: 3,url:'panele'},
          {id:1,nazwa: 'Słupek ogrodzeniowy 60x40 H-2200',cena: 48,waga: 3,url:'panele'},
          {id:2,nazwa: 'Słupek ogrodzeniowy 60x40 H-2300',cena: 48,waga: 3,url:'panele'},
          {id:3,nazwa: 'Słupek ogrodzeniowy 60x40 H-2400',cena: 48,waga: 3,url:'panele'},
          {id:4,nazwa: 'Słupek ogrodzeniowy 60x40 H-2600',cena: 48,waga: 3,url:'panele'},
          {id:5,nazwa: 'Słupek ogrodzeniowy 60x40 H-2800',cena: 48,waga: 3,url:'panele'},
          {id:6,nazwa: 'Słupek ogrodzeniowy 60x40 H-3000',cena: 48,waga: 3,url:'panele'},
        ],
        price_table: [
          {id:0,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:1,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:2,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:3,ilosc: 0,c_j: 0,c_n:0,c_b:0},
          {id:4,ilosc: 0,c_j: 0,c_n:0,c_b:0},
        ],
    }
    ),
     watch: {
      loader () {
        const l = this.loader;
        this[l] = !this[l];
        setTimeout(() => (this[l] = false), 3000);
        this.loader = null;
      },
    },

   beforeMount(){
    this.calculate()
    },
    methods:{
      wysylaj: function(e) {

    this.templateParams.p1 = this.panele[this.panel_id].nazwa
    this.templateParams.p2 = this.podmurowka[this.podmurowka_id].nazwa
    this.templateParams.p3 = this.laczniki[this.laczniki_id].nazwa
    this.templateParams.p4 = this.slupki[this.slupki_id].nazwa
    this.templateParams.p1przesla = this.price_table[0].ilosc
    this.templateParams.p2przesla = this.price_table[1].ilosc
    this.templateParams.p3przesla = this.price_table[2].ilosc
    this.templateParams.p4przesla = this.price_table[3].ilosc
    this.templateParams.p5przesla = this.price_table[0].ilosc
    this.templateParams.p1cj = this.price_table[0].c_j
    this.templateParams.p2cj = this.price_table[1].c_j
    this.templateParams.p3cj = this.price_table[2].c_j
    this.templateParams.p4cj = this.price_table[3].c_j
    this.templateParams.p5cj = this.price_table[4].c_j
    this.templateParams.p1cn = this.price_table[0].c_n
    this.templateParams.p2cn = this.price_table[1].c_n
    this.templateParams.p3cn = this.price_table[2].c_n
    this.templateParams.p4cn = this.price_table[3].c_n
    this.templateParams.p5cn = this.price_table[4].c_n
    this.templateParams.p1cb = this.price_table[0].c_b
    this.templateParams.p2cb = this.price_table[1].c_b
    this.templateParams.p3cb = this.price_table[2].c_b
    this.templateParams.p4cb = this.price_table[3].c_b
    this.templateParams.p5cb = this.price_table[4].c_b
    this.templateParams.suma = this.koszyk
    this.templateParams.dl_og =  this.dl_og

    if(this.montaz == 0){
        this.templateParams.p5przesla = ''
        this.templateParams.p5 = ''
        this.templateParams.p5cb = ''
        this.templateParams.p5cn = ''
        this.templateParams.p5cj = ''
    }

    this.wyslijWiadomosc(e)
    },
    wyslijWiadomosc: (e) => {
      emailjs.send('service_eo93tkg', 'template_13rpexb', e, 'user_7rKUwlgUE3sdslLCLbklC')
    .then(function(response) {
       console.log('SUCCESS!', response.status, response.text);
       console.log(e);
    }, function(error) {
       console.log('FAILED...', error);
    });
  },
      calculate(){
      this.przesla = Math.round(((this.dl_og)/2.6)+0.49)
      this.price_table[0].ilosc = this.przesla
      this.price_table[1].ilosc = this.przesla
        if (this.laczniki_id == 1 || this.laczniki_id == 3 ) {
        this.price_table[2].ilosc = this.przesla*2}
        else this.price_table[2].ilosc = this.przesla
      this.price_table[3].ilosc = this.przesla
      this.price_table[4].ilosc = this.przesla
      this.price_table[0].c_j = Math.round((this.panele[this.panel_id].cena * this.marza)*100)/100
      this.price_table[1].c_j = Math.round((this.podmurowka[this.podmurowka_id].cena * this.marza)*100)/100
      this.price_table[2].c_j = Math.round((this.laczniki[this.laczniki_id].cena * this.marza)*100)/100
      this.price_table[3].c_j = Math.round((this.slupki[this.slupki_id].cena * this.marza)*100)/100
      this.price_table[4].c_j = Math.round(((2500/((this.przesla)*2.6))+(50*2.6))*100)/100
      this.price_table[0].c_n = Math.round((this.price_table[0].c_j * this.price_table[0].ilosc)*100)/100
      this.price_table[1].c_n = Math.round((this.price_table[1].c_j * this.price_table[1].ilosc)*100)/100
      this.price_table[2].c_n = Math.round((this.price_table[2].c_j * this.price_table[2].ilosc)*100)/100
      this.price_table[3].c_n = Math.round((this.price_table[3].c_j * this.price_table[3].ilosc)*100)/100
      this.price_table[4].c_n = Math.round((this.price_table[4].c_j * this.price_table[4].ilosc)*100)/100
      this.price_table[0].c_b = Math.round((this.price_table[0].c_n * 1.23)*100)/100
      this.price_table[1].c_b = Math.round((this.price_table[1].c_n * 1.23)*100)/100
      this.price_table[2].c_b = Math.round((this.price_table[2].c_n * 1.23)*100)/100
      this.price_table[3].c_b = Math.round((this.price_table[3].c_n * 1.23)*100)/100
      if(this.montaz==1){
        this.price_table[4].c_b = Math.round((this.price_table[4].c_n * 1.23)*100)/100
        this.templateParams.p5 = "Montaż przęsła"
      }else{
        // this.price_table[4].c_j = 0
        this.price_table[4].c_b = 0
        }
      this.koszyk = Math.round((this.price_table[0].c_b + this.price_table[1].c_b + this.price_table[2].c_b + this.price_table[3].c_b + this.price_table[4].c_b)*100)/100 
      },
    },
  }
</script>

<style lang="scss">

.container{
width: 100%;
}

.kolumna{
border-right: solid black 1px
}
.srodek{
  text-align:center;
}
div .iconsfooter
{
  align-items: center;
  justify-content: center;
  vertical-align: middle;
  height:100%;
  padding-left:40px;
}

div .iconsfooter span
{
  vertical-align: middle;
  height:100%;
}

div .iconsfooter i
{
  margin-right:5px;
  vertical-align: middle;
  display:inline-block;
  height:100%;
}
div .color-picker-box
{
display:flex;
justify-content: space-evenly;
margin-top:20px;
margin-bottom:40px;
max-width:100%;
flex-wrap: wrap;
}

div .color-picker
{
border-radius: 10px;
border:solid black 1px;
padding:50px 50px;
margin:5px;
color:white;
background-color: black;
}

div .color-picker:hover
{
opacity:0.6;
cursor:pointer;
}
   .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }

.sitetop
{
  display:block;
  line-height:3rem;
  font-size: 2rem;
  font-weight: 600;
  letter-spacing: 0.2rem;
  text-transform: uppercase;
  color:rgb(12, 108, 240);
  text-align:center;
}

.sitebot
{
  display:block;
  line-height:1.5rem;
  font-size: 1rem;
  font-weight: 500;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
  padding-bottom: 10px;
}

div .calcsection{
  border-radius: 15px;
  padding:20px 10px;
  margin:10px 0px;
  background-color:#0C6CF0
}

.footericon{
  font-size:30px;
  padding-left:20px;
}

.pricetext{
  font-size:22px;
  font-weight: 600;
}

  @media screen and (max-width: 840px){


.sitetop
{
  display:block;
  line-height:1.3rem;
  font-size: 1.2rem;
  font-weight: 900;
  letter-spacing: 0.1rem;
  text-transform: uppercase;
  text-align: center;
}

.sitemid
{
  display:block;
  line-height:1.2rem;
  font-size: 1.1rem;
  font-weight: 600;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
  padding-bottom: 10px;
}

.sitebot
{
  display:block;
  line-height:1rem;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.05rem;
  text-transform: uppercase;
  padding-bottom: 10px;
}

div .calcsection{
  border-radius: 15px;
  padding:1px 5px;
  margin:10px 0px;
  background-color:#0C6CF0
}

.pricetext{
  font-size:16px;
  font-weight: 600;
}
.footericon{
  font-size:8px;
  padding-left:20px;
}

}



</style>