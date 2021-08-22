<template>


 <v-container class="">
   <!-- <v-row class=""><h1 class="siteheader">Kalkulator bram i furtek</h1></v-row> -->
   <v-row>
     <v-col class="gatecalculator">
       <!-- <img src="../../src/assets/logocz.jpg" alt=""> -->
       <!-- <model-stl width='300' height='300' src="../../src/assets/f2.stl"></model-stl> -->
       <!-- <model-stl width='1200' height='1200' src="../../src/assets/f2.stl"></model-stl> -->
       <!-- <span class="sitetop">Kalkulator bram i furtek</span> -->
       <v-card class="calcsection color-gr2">
         <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        1. RODZAJ I WYMIARY
      </span>
    </v-card-title>
         <v-row>
        <v-col>
          <p class="sitebot">Konstrukcja
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
        A. Wybierz interesujący Cię produkt
        <br>
        B. Poniżej pojawi się przykładowa wizualizacja o standardowych wymiarach.
        <br>
        C. Przytrzymaj lewy przycisk myszy aby obracać, użyj scrolla myszy aby oddalać i przybliżać obraz.
        <br>
        D. Dostosuj wysokość i szerokość
        <br>
        D. U dołu ekranu przelicza się waga oraz cena.
      </span>
    </v-tooltip>
         </p>
          <v-select @input="ustawiaj_opcje()" :items="rodzaj_produktu" v-model="rodzaj_produktu_wybrane_id" item-value="id" item-text="nazwa" label="Produkt" outlined></v-select>
      <p class="sitebot">Szerokośc / Światło w mb</p>
      <v-slider v-model="swiatlo_bramy" @input="calculate()" step="0.1" thumb-label="always" min="1" max="8" color="black"></v-slider>
      <v-text-field type="number" outlined single-line step="0.1" v-model="swiatlo_bramy"></v-text-field>
      <p class="sitebot">Wysokość od gruntu</p>
      <v-slider v-model="wys" @input="calculate()" step="0.1" thumb-label="always" min="0.8" max="2.4" color="black"></v-slider>
      <v-text-field type="number" outlined single-line step="0.1" v-model="wys"></v-text-field>
         </v-col>
         <v-col>
           <p class="sitebot">Wizualizacja poglądowa produktu
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
        <div class="trzyde">
         <model-stl v-if="rodzaj_produktu_wybrane_id==0 && selection==0" backgroundAlpha="0" height="300" src="img/fpanel.stl"></model-stl>
         <model-stl v-if="rodzaj_produktu_wybrane_id==0 && selection==1" backgroundAlpha="0" height="300" src="img/fpalisada.stl"></model-stl>
         <model-stl v-if="rodzaj_produktu_wybrane_id==2 && selection==0" backgroundAlpha="0" height="300" src="img/bdwpanel.stl"></model-stl>
         <model-stl v-if="rodzaj_produktu_wybrane_id==2 && selection==1" backgroundAlpha="0" height="300" src="img/bdwpalisada.stl"></model-stl>
       </div>
         </v-col>
         </v-row>
      </v-card>
      <v-card class="calcsection color-gr2">
<v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        2. KONSTRUKCJA
      </span>
    </v-card-title>
        <p class="sitebot">Materiał wykonania
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
       <v-select @input="calculate()" :items="rodzaj_stali" v-model="rodzaj_stali_wybrane_id" item-value="id" item-text="nazwa" label="Materiał" outlined></v-select>
        <p class="sitebot">Profil konsturkcji Ramy</p>
      <v-select @input="calculate()" :items="stal" item-text="nazwa" item-value="id" v-model ="qwe" label="Profil do budowy ramy" outlined></v-select>
      <p class="sitebot">Słup 1</p>
      <v-select @input="calculate()" :items="stal" item-text="nazwa" item-value="id" v-model ="slup1" label="Słup numer 1" outlined ></v-select>
      <p class="sitebot">Słup 2</p>
      <v-select @input="calculate()" :items="stal" item-text="nazwa" item-value="id" v-model ="slup2" label="Słup numer 2" outlined ></v-select>

      </v-card>



      <v-card class="calcsection color-gr2">
    <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        3. WYPEŁNIENIE
      </span>
    </v-card-title>
    <p class="sitebot">Dopasuj wypełnienie konstrukcji
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
        A. Wybierz wypełnienie panelem lub Palisadą - zmieni się wizualizacja
        <br>
        B. Ramka dołem to dwa dodatkowe profile dla względów estetycznych, aby zastosować panel z takimi samymi przetłoczeniami jakiego użyto przy ogrodzeniu.
        <br>
        C. Najpopularniejsza palisada wykonywana jest z profila 80x20x1,5
        <br>
        D. Wypełnienie mocno wpływa na wagę a co za tym idzie na cenę konstrukcji.
        <br>
        D. Dodając większą przerwę pomiędzy profilami obniżasz wagę oraz cenę konstrukcji.
      </span>
    </v-tooltip>
         </p>
         <v-tabs color="black" v-model="selection" grow>
      <v-tab>
        <v-icon left>
          mdi-focus-field
        </v-icon>
        Panel
      </v-tab>
      <v-tab>
        <v-icon left>
          mdi-equal-box
        </v-icon>
        Palisada
      </v-tab>
      <v-tab-item>
        <v-card flat color="none" text="red">
          <v-card-text>
            <p class="mb-0">
              Wypełnienie wybranym panelem ogrodzeniowym 46 drutów pionowych oko 50/200, w cenie 10 zawijek oraz wkrętów. Ramka dołem to dwa profile poziome w świetle bramy poniżej panela ogrodzeniowego.
            </p>
            <br>
            <v-select @input="calculate()" :items="panele" v-model="rodzaj_paneli_wybrane_id" item-text="nazwa" item-value="id" label="Panele ogrodzeniowe" outlined></v-select>
        <v-checkbox @input="calculate()" v-model="ramka" label="Ramka dołem" color="blue" value="1" ></v-checkbox>
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item>
        <v-card flat color="none" text="red">
          <v-card-text>
            <p class="mb-0">
              Wypełnienie w ceowniku 25x25x2. Wybierz profil i jego ułożenie na wypełnienie bramy.
            </p>
            <br>
      <v-select @input="calculate()" :items="stal" item-text="nazwa" item-value="id" v-model ="qwe2" label="Profil wypełnienia" outlined ></v-select>
      <v-slider @input="calculate()" v-model="odstep_miedzy_profilami" label="Przerwa między profilami (mm)" step="1" thumb-label="always" min="15" max="200" color="black"></v-slider>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
         </v-card>

      <!-- <div v-if="rys_tech==1">
      <img src="" alt="">
      </div>
      <div v-if="info_tech==1">
      <p>Światło bramy: {{swiatlo_bramy}} mb</p>
      <p>Przeciwwaga: {{pw}}</p>
      <p>Całkowita długość bramy {{cdb}} mb</p>
      <br>
      <p>Profil rama {{obwod}} mb</p>
      <p>Profil przeciwwaga {{obwodpw}} mb</p>
      <p>Profile na konstrukcję razem mb {{ profil_konstrukcja_mb }} mb || {{  profil_konstrukcja_waga }} kg</p>
      <br>
      <p>Szyna 80x80x5 {{szyna_mb}} mb || {{szyna_kg}} kg</p>
      <p>slup1 {{slup1_kg}} kg</p>
      <p>slup2 {{slup2_kg}} kg</p>
      uslugi i akcesoria razem {{uslugi_i_akcesoria_pln}}
      <br>
      <p>Wysokość do wypełnienia (mb) {{((wys*1000-((stal[this.qwe].a*2)+160)))/1000}} </p>
      <p v-if="selection==1">ceownik {{ceownik_mb}} mb || {{ceownik_kg}} kg</p>
      <p v-if="selection==1">ilość profili do wypełnienia {{wyp_szt}} </p>
      <p v-if="selection==1">ilość mb do wypełnienia {{wyp_mb}} || {{wyp_kg}} kg</p>
      <p>lakierowanie :  {{this.lakier_cena}}</p>

      </div> -->
      <!-- <div v-if="podp==1">
        <p>Jeśli jest taka możlwość zamawiaj bramę przesuwną zamiast dwuskrzydłowej</p>
        <p>Podczas montażu bramy dwuskrzydłowej paamiętaj, że będzie ściągać słupy do środka</p>
        <p>Giętkość profila obliczysz ze wzoru .... </p>
      </div> -->

     <!-- </v-col>
     <v-col> -->
       <v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        4. USŁUGI I AKCESORIA
      </span>
    </v-card-title>
    <p class="sitebot">Dobierz usługi i akcesoria
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
         <v-checkbox v-if="rodzaj_stali_wybrane_id==0" v-on="calculate()" v-model="cynk" label="Cynkowanie" color="blue" value="1"></v-checkbox>
        <v-checkbox v-on="calculate()" v-model="lakier" label="Lakierowanie proszkowe" color="blue" value="1"></v-checkbox>
        <v-checkbox v-on="calculate()" v-model="transport_do_klienta" label="Transport" color="blue" value="1"></v-checkbox>
        <v-checkbox v-on="calculate()" v-model="montaz" label="Montaż" color="blue" value="1"></v-checkbox>
        <v-select v-if="rodzaj_produktu_wybrane_id==0" @input="policz_akcesoria()" multiple deletable-chips chips :items="akcesoria_furtka" item-text="nazwa" item-value="id" v-model ="akcf" label="Akcesoria do furtki" outlined item-disabled="customdisabled"></v-select>
        <v-select v-if="rodzaj_produktu_wybrane_id==1" @input="policz_akcesoria1()" multiple :items="akcesoria_bprz" item-text="nazwa" item-value="id" v-model ="akc_bprz" label="Akcesoria do bramy przesuwnej" outlined item-disabled="customdisabled"></v-select>
        <v-select v-if="rodzaj_produktu_wybrane_id==2" @input="policz_akcesoria2()" multiple :items="akcesoria_bdw" item-text="nazwa" item-value="id" v-model ="akc_bdw" label="Akcesoria do bramy dwuskrzydłowej" outlined item-disabled="customdisabled"></v-select>
      <!-- <v-checkbox v-model="info_tech" label="Pokaż informacje szczegółowe" color="blue" value="1"></v-checkbox> -->
    </v-card>


<v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        5. ZAPISZ WYCENĘ
      </span>
    </v-card-title>
    <p>5.Zarezerwuj cenę na 7 dni
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
       A
       <br>
       B
       <br>
       C
        <br>
       D
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
          <br>
          <v-btn block :disabled="isActive" color="primary" @click="wysylaj(templateParams)">Wyślij</v-btn>
           <v-alert v-if="isactivealert" class="mt-4" type="success">
      Wycena została wysłana
    </v-alert>
</v-card>

       <!-- <span class="sitetop">Zdjęcia i wizualizacje</span>
       <v-card class="calcsection color-gr2">
       <v-card-title class="text-center justify-center py-6">
      <span class="sitemid">
        3D RENDER
      </span>
    </v-card-title>
    
    </v-card> -->
    </v-col>
   </v-row>
    <v-bottom-navigation height="64px" v-model="value" fixed="true">
      <div class="iconsfooter"><v-icon color="blue" class="footericon">mdi-cash-multiple</v-icon><span class="pricetext">{{Math.round(suma_pln*1.23)}} PLN</span></div>
      <div class="iconsfooter"><v-icon color="blue" class="footericon">mdi-weight-kilogram</v-icon><span class="pricetext">{{suma_kg}} KG</span></div>
  </v-bottom-navigation>


  </v-container>

</template>

<script>
import { ModelStl } from 'vue-3d-model';
import emailjs from 'emailjs-com';
export default {

components: { ModelStl },
  mounted(){
    this.ustawiaj_opcje(),
    this.policz_akcesoria(),
    this.calculate()
  },
 data: () => ({
  //     style: {
  //   color: 'red',
  //   fontSize: this.swiatlo_bramy,
  // },

      templateParams:{
      name: '',
      notes: 'Check this out!',
      message:'Regulamin usług montażowych znajduje się na www.modernbau.info, prosimy o zapoznanie się z zasadami',
      to_name:'X - STAL',
      from_name:'',
      number:'42/06/2021',
      imie:'',
      nazwisko:'',
      phone:'',
      miejscowosc: '',
      ulica:'',
      numer:'',
      material:'',
      rama:'',
      rodzaj:'',
      wys:'',
      szer:'',
      wypelnienie:'',
      slup1:'',
      slup2:'',
      waga:'',
      cena:'',
      transport:'',
      lakierowanie:'',
      cynkowanie:'',
      montaż:'',
      cena_montazu:'',
      },
      isActive:false,
      isactivealert:false,
      rodzaj_stali_wybrane_id: 1, // id itemu z selecta "materiał"
      rodzaj_paneli_wybrane_id: 0, // id itemu z selecta "panele ogrodzeniowe"
      rodzaj_produktu_wybrane_id: 0,
      pw:0, // przeciwwaga w mb obliczana w calculate()
      cdb:0, // calkowita dlugosc bramy w mb obliczana w calculate()
      wys: 1.4, // wysokosc bramy suwak w mb
      swiatlo_bramy: 1, // swiatlo bramy suwak w mb
      qwe: 5, // id profila do budowy ramy
      qwe2: 2, // id profila do wypełnienia
      slup1:15,
      slup2:15,
      uslugi_i_akcesoria_pln:0,
      slup1_kg:0,
      slup2_kg:0,
      ramka_dolem: 0,
      ramka:"1", // zaznaczyony checkbox
      montaz:0,
      testingfor:0,
      obwod: 0,
      obwodpw:0,
      ceownik_mb:0,
      ceownik_kg:0,
      suma_pln:0,
      panele_cena:0, // plus zawijki i wkręty
      lakiernia: 35, // lakierowanie za mb
      ocynkownia: 3.1, // cynkowanie za mb
      narzut: 2, // narzut mnożnik
      akcf:0,
      akc_bdw:null,
      akc_bprz:null,
      usl1:[0,1,2],
      rys_tech:1,
      info_tech:0,
      zebatki:0,
      wozki:0,
      naped:0,
      zabudowy:0,
      kotwy:0,
      podp:0,
      antaba:0,
      transport_do_klienta:0,
      cynk:0,
      lakier:0,
      cynk_cena:0,
      lakier_cena:0,
      szyna_kg:0,
      transport_cena:100,
      wyp_szt: 0,
      suma_kg : 0,
      selection : 0, // podaje która zakładka wyboru jest aktywna 0 lub 1
      wypeln: 0,
      odstep_miedzy_profilami: 20,
      profil_konstrukcja_mb: 0,
      profil_konstrukcja_waga: 0,
      suma_akcesoria_pln:0,
      rodzaj_stali: [
        {id:0,nazwa:'Profile z czarnej stali',cena_za_kg:6.3,gestosc:7600},
        {id:1,nazwa:'Profile ocynkowane',cena_za_kg:8.5,gestosc:7600},
        // {id:2,nazwa:'Stal nierdzewna',cena_za_kg:10,gestosc:7800},
        // {id:3,nazwa:'Aluminium',cena_za_kg:11,gestosc:2700},
        ],
        uslugi: [
        {id:0,nazwa:'Cynkowanie',cena:60,customdisabled:false},
        {id:1,nazwa:'Lakierowanie',cena:70,customdisabled:false,},
        {id:2,nazwa:'Transport',cena:30,customdisabled:false,},
        {id:3,nazwa:'Montaż',cena:3000,customdisabled:false,},
        {id:4,nazwa:'Wylanie stopy',cena:3000,customdisabled:true,},
        ],
        akcesoria_furtka: [
        {id:0,nazwa:'zamek wąski wpuszczany 90mm zapadka',cena:14.23,customdisabled:false},
        {id:1,nazwa:'zamek wąski wpuszczany 90mm rolka',cena:14.23,customdisabled:false},
        {id:2,nazwa:'klamka 90mm ZJ',cena:7.80,customdisabled:false},
        {id:3,nazwa:'klamka 90mm TP',cena:21.96,customdisabled:false},
        {id:4,nazwa:'klamka - gałka 90mm ZJ',cena:17,customdisabled:false},
        {id:5,nazwa:'gałka - gałka 90mm ZJ',cena:9,customdisabled:false}, 
        {id:6,nazwa:'klamka - gałka 90mm TP',cena:17,customdisabled:false},
        {id:7,nazwa:'gałka - gałka 90mm TP',cena:9,customdisabled:false},
        {id:8,nazwa:'wkładka z kluczykiem "Standard"',cena:9.80,customdisabled:false},
        {id:9,nazwa:'wkładka z kluczykiem "Gerda"',cena:11,customdisabled:false},
        {id:10,nazwa:'zaczep ZFP2 Kolor',cena:18,customdisabled:false},
        {id:11,nazwa:'kaseta elektrozaczepu kolor',cena:33.05,customdisabled:false},
        {id:12,nazwa:'elektrozaczep R3',cena:36.59,customdisabled:false},
        {id:13,nazwa:'elektrozaczep R4',cena:36.59,customdisabled:false},
        {id:14,nazwa:'antaba spawana',cena:75,customdisabled:false},
        {id:15,nazwa:'maskownice / daszki do słupków',cena:3,customdisabled:false},
        {id:16,nazwa:'zawiasy przykręcane 55x75',cena:20,customdisabled:false},
        {id:17,nazwa:'zawiasy przykręcane 80x80',cena:20,customdisabled:false},
        ],
        akcesoria_bdw: [
        {id:0,nazwa:'zamek wąski wpuszczany 90mm zapadka',cena:14.23,customdisabled:false},
        {id:1,nazwa:'zamek wąski wpuszczany 90mm rolka',cena:14.23,customdisabled:false},
        {id:2,nazwa:'napęd bramy dwuskrzydłowej',cena:1000,customdisabled:false,}, // normalna cena zakupu 1350 zaniżona ponieważ liczy x2
        {id:3,nazwa:'montaż napędu',cena:600,customdisabled:false,},
        {id:4,nazwa:'klamka 90mm ZJ',cena:7.80,customdisabled:false},
        {id:5,nazwa:'klamka 90mm TP',cena:21.96,customdisabled:false},
        {id:6,nazwa:'zaczep furtki ZFP/2 TP',cena:18.00,customdisabled:false},
        {id:7,nazwa:'wrzeciądz przelotowy pod kłódkę',cena:11.00,customdisabled:false},
        {id:8,nazwa:'wkładka z kluczykiem "Standard"',cena:9.80,customdisabled:false},
        {id:9,nazwa:'wkładka z kluczykiem "Gerda"',cena:11,customdisabled:false},
        {id:10,nazwa:'antaba spawana',cena:75,customdisabled:false},
        {id:11,nazwa:'maskownice / daszki do słupków',cena:3,customdisabled:false},
        {id:12,nazwa:'zawiasy przykręcane 80x80',cena:20,customdisabled:false},
        {id:13,nazwa:'zawiasy przykręcane 100x100',cena:24.30,customdisabled:false},
        {id:14,nazwa:'stopka / ogranicznik ocynkowany pod rygiel',cena:10.50,customdisabled:false},
        {id:15,nazwa:'stopka / ogranicznik ocynkowany bez rygla',cena:10.50,customdisabled:false},
        {id:16,nazwa:'rygiel wąski 420 TP',cena:11.34,customdisabled:false},
        {id:17,nazwa:'rygiel wąski 220 TP',cena:10.15,customdisabled:false},
        {id:18,nazwa:'zasuwa standard ocynk TP',cena:18.48,customdisabled:false},
        ],
        akcesoria_bprz: [
        {id:0,nazwa:'słup stabilizujący 60x60x2',cena:150,customdisabled:false},
        {id:1,nazwa:'napęd słupkowy z kogutem',cena:950,customdisabled:false,}, // normalna cena zakupu 1350 zaniżona ponieważ liczy x2
        {id:2,nazwa:'montaż napędu',cena:500,customdisabled:false,},
        {id:3,nazwa:'zębatki',cena:90,customdisabled:false,}, // 5.6 mb zakładamy 5mb zębatek
        {id:4,nazwa:'2 Piloty',cena:82,customdisabled:false,},
        {id:5,nazwa:'2 Fotokomórki',cena:170,customdisabled:false,},
        {id:6,nazwa:'wózki poliamidowe',cena:182,customdisabled:false,},
        {id:7,nazwa:'zabudowy wózków',cena:24,customdisabled:false,},
        {id:8,nazwa:'kotwy do montażu',cena:24.72,customdisabled:false,},
        {id:9,nazwa:'chwytak bramy UB/PA TP',cena:5,customdisabled:false,},
        {id:10,nazwa:'chwytak bramy UB2PA 60cm TP',cena:40,customdisabled:false,},
        {id:11,nazwa:'chwytak bramy UN80 z dwoma rolkami i odbojnikiem TP',cena:30.80,customdisabled:false,},
        {id:12,nazwa:'najazd dolny chwytak bramy UN80 TP',cena:18,customdisabled:false,},
        {id:13,nazwa:'rolka stabilizująca',cena:10,customdisabled:false,},
        {id:14,nazwa:'rolka najazdu do szyny',cena:25,customdisabled:false,},
        {id:15,nazwa:'rolka najazdu na słupek końcowy',cena:25,customdisabled:false,},
        {id:16,nazwa:'zamek hakowy',cena:29.14,customdisabled:false,},
        {id:17,nazwa:'antaba',cena:75,customdisabled:false,},
        ],
        rodzaj_produktu: [
        {id:0,nazwa:'Furtka',narzut:2, montaz:400},
        {id:1,nazwa:'Brama przesuwna',narzut:2, montaz: 2000},
        {id:2,nazwa:'Brama dwuskrzydłowa',narzut:2, montaz: 2000},
        ],
      stal: [
          {id:0,nazwa: '40x40x1.5 mm',a: 40,b: 40,gr:1.5,kategoria:'profile zamknięte'},
          {id:1,nazwa: '40x40x2.0 mm',a: 40,b: 40,gr:2.0,kategoria:'profile zamknięte'},
          {id:2,nazwa: '60x20x1.5 mm',a: 60,b: 20,gr:1.5,kategoria:'profile zamknięte'},
          {id:3,nazwa: '60x20x2.0 mm',a: 60,b: 20,gr:2,kategoria:'profile zamknięte'},
          {id:4,nazwa: '60x40x1.5 mm',a: 60,b: 40,gr:1.5,kategoria:'profile zamknięte'},
          {id:5,nazwa: '60x40x2.0 mm',a: 60,b: 40,gr:2,kategoria:'profile zamknięte'},
          {id:6,nazwa: '80x20x1.5 mm',a: 80,b: 20,gr:1.5,kategoria:'profile zamknięte'},
          {id:7,nazwa: '80x20x2.0 mm',a: 80,b: 20,gr:2,kategoria:'profile zamknięte'},
          {id:8,nazwa: '80x40x1.5 mm',a: 80,b: 40,gr:1.5,kategoria:'profile zamknięte'},
          {id:9,nazwa: '80x40x2.0 mm',a: 80,b: 40,gr:2,kategoria:'profile zamknięte'},
          {id:10,nazwa: '100x20x1.5 mm',a: 100,b: 20,gr:1.5,waga:0,kategoria:'profile zamknięte'},
          {id:11,nazwa: '100x100x2.0 mm',a: 100,b: 100,gr:2,kategoria:'profile zamknięte'},
          {id:12,nazwa: '100x100x3.0 mm',a: 100,b: 100,gr:3,kategoria:'profile zamknięte'},
          {id:13,nazwa: '100x100x4.0 mm',a: 100,b: 100,gr:4,kategoria:'profile zamknięte'},
          {id:14,nazwa: '60x60x1.5 mm',a: 60,b: 60,gr:1.5,kategoria:'profile zamknięte'},
          {id:15,nazwa: '60x60x2.0 mm',a: 60,b: 60,gr:2,kategoria:'profile zamknięte'},
          {id:16,nazwa: '60x60x3.0 mm',a: 60,b: 60,gr:3,kategoria:'profile zamknięte'},
          {id:17,nazwa: '80x80x3.0 mm',a: 80,b: 80,gr:3,kategoria:'profile zamknięte'},
          {id:18,nazwa: '80x80x4.0 mm',a: 80,b: 80,gr:4,kategoria:'profile zamknięte'},
          {id:19,nazwa: 'Brak',a: 0,b: 0,gr:4,kategoria:'profile zamknięte'},
        ],
      panele: [
          {id:0,nazwa: '123 fi 4',cena: 48,waga: 3,kategoria:'panele'},
          {id:1,nazwa: '123 fi 5',cena: 68,waga: 5,kategoria:'panele'},
          {id:2,nazwa: '153 fi 4',cena: 58,waga: 4,kategoria:'panele'},
          {id:3,nazwa: '153 fi 5',cena: 78,waga: 6,kategoria:'panele'},
          {id:4,nazwa: 'Brak',cena: 0,waga: 0,kategoria:'panele'},
        ],

      calculate: function(){
          this.obwod = Math.round((this.swiatlo_bramy*2 + this.wys*2)*100)/100
          this.profil_konstrukcja_mb = this.obwodpw+this.obwod+this.ramka_dolem
          this.profil_konstrukcja_waga = Math.round((((((this.stal[this.qwe].a*2/1000)+(this.stal[this.qwe].b*2/1000))*this.stal[this.qwe].gr/1000)*this.rodzaj_stali[this.rodzaj_stali_wybrane_id].gestosc)*(this.profil_konstrukcja_mb))*100)/100
          this.slup1_kg = (((((this.stal[this.slup1].a*2/1000)+(this.stal[this.slup1].b*2/1000))*this.stal[this.slup1].gr/1000)*this.rodzaj_stali[this.rodzaj_stali_wybrane_id].gestosc)*(this.wys+0.6))
          this.slup2_kg = (((((this.stal[this.slup2].a*2/1000)+(this.stal[this.slup2].b*2/1000))*this.stal[this.slup2].gr/1000)*this.rodzaj_stali[this.rodzaj_stali_wybrane_id].gestosc)*(this.wys+0.6))
          this.calculate_kg()
          if (this.selection == 1){
          this.ramka_dolem = 0
          this.ceownik_mb = ((this.wys*1000-((this.stal[this.qwe].a*2)+160))*2)/1000
          this.ceownik_kg = this.ceownik_mb*1.22
          this.wyp_szt = (((this.wys*1000-((this.stal[this.qwe].a*2)+160-this.odstep_miedzy_profilami)))/1000)/((this.stal[this.qwe2].a+this.odstep_miedzy_profilami)/1000)
          this.wyp_mb = (this.swiatlo_bramy-(this.stal[this.qwe].a*2)/1000)*(((this.wys*1000-((this.stal[this.qwe].a*2)+160-this.odstep_miedzy_profilami)))/1000)/((this.stal[this.qwe2].a+this.odstep_miedzy_profilami)/1000)
          this.wyp_kg = ((((this.stal[this.qwe2].a*2/1000)+(this.stal[this.qwe2].b*2/1000))*this.stal[this.qwe2].gr/1000)*this.rodzaj_stali[this.rodzaj_stali_wybrane_id].gestosc)*(this.wyp_mb)
          }else{
            if(this.ramka == 1){this.ramka_dolem = this.swiatlo_bramy*2}else{this.ramka_dolem = 0}
            this.ceownik_mb = 0
            this.ceownik_kg = 0
            this.wyp_szt = 0
            this.wyp_mb = 0
            if(this.swiatlo_bramy < 2.5){
                this.wyp_kg = this.panele[this.rodzaj_paneli_wybrane_id].waga
                this.panele_cena = this.panele[this.rodzaj_paneli_wybrane_id].cena
                }
                else if(this.swiatlo_bramy < 5)
                    {
                    this.wyp_kg = this.panele[this.rodzaj_paneli_wybrane_id].waga*2
                    this.panele_cena = this.panele[this.rodzaj_paneli_wybrane_id].cena*2
                    }
                    else if(this.swiatlo_bramy < 7.5)
                          {
                           this.wyp_kg = this.panele[this.rodzaj_paneli_wybrane_id].waga*3
                          this.panele_cena = this.panele[this.rodzaj_paneli_wybrane_id].cena*3
                            }
          }

          if (this.cynk==1 && this.rodzaj_stali_wybrane_id==0) {
            this.cynk_cena = this.transport_cena + ((this.suma_kg*1.05) * 3)
          }else this.cynk_cena = 0

          if (this.lakier==1) {
            this.lakier_cena = (((this.swiatlo_bramy*this.wys)*2) * this.lakiernia)
          }else this.lakier_cena = 0
          this.calculate_pln()
      },
    wysylaj: function(e) {
      this.templateParams.wys = this.wys;
      this.templateParams.material = this.rodzaj_stali[this.rodzaj_stali_wybrane_id].nazwa;
      this.templateParams.szer = this.swiatlo_bramy;
      this.templateParams.slup1 = this.stal[this.slup1].nazwa;
      this.templateParams.slup2 = this.stal[this.slup2].nazwa;
      this.templateParams.wysokoscslupa = this.wys + 0.6;
      this.templateParams.cynkowanie = this.rodzaj_stali_wybrane_id == 0 && this.cynk== 1 ? "Tak" : "Nie";
      this.templateParams.transport = this.transport_do_klienta == 1 ? "Tak" : "Nie";
      this.templateParams.lakierowanie = this.lakier == 1 ? "Tak" : "Nie";
      this.templateParams.montaz = this.montaz == 1 ? "Tak" : "Nie";
      this.templateParams.cena = Math.round((this.suma_pln*1.23))
      this.templateParams.waga = this.suma_kg
      this.templateParams.cena_montazu = "1000 i nie"
      this.templateParams.rama = this.stal[this.qwe].nazwa;
      this.templateParams.rodzaj = this.rodzaj_produktu[this.rodzaj_produktu_wybrane_id].nazwa;
      if(this.selection == 0)
      {
      this.templateParams.wypelnienie = 'Panel ogrodzeniowy ' + this.panele[this.rodzaj_paneli_wybrane_id].nazwa
      }else {
        this.templateParams.wypelnienie = 'Palisada stalowa ' + this.stal[this.qwe2].nazwa
        }
      if(this.ramka == 1 && this.selection == 0)
        {this.templateParams.wypelnienie += ' *plus ramka z podwójnego profila dołem';
          console.log('ramka jest dołem')
          }

        this.templateParams.akcesoria = '';
      if(this.rodzaj_produktu_wybrane_id == 0){
          for (let i = 0; i < this.akcf.length; i++){
       this.templateParams.akcesoria += this.akcesoria_furtka[this.akcf[i]].nazwa + '  ****  ';
         }
      }else if(this.rodzaj_produktu_wybrane_id == 1){
         for (let i = 0; i < this.akc_bprz.length; i++){
       this.templateParams.akcesoria += this.akcesoria_bprz[this.akc_bprz[i]].nazwa + ', ';
         }
      }else if(this.rodzaj_produktu_wybrane_id == 2){
          for (let i = 0; i < this.akc_bdw.length; i++){
       this.templateParams.akcesoria += this.akcesoria_bdw[this.akc_bdw[i]].nazwa + ', ';
         }
      }

    this.wyslijWiadomosc(e);
    this.isDisabled();
    },
    wyslijWiadomosc: (e) => {
      emailjs.send('service_eo93tkg', 'template_ehe5afj', e, 'user_7rKUwlgUE3sdslLCLbklC')
    .then(function(response) {
       console.log('SUCCESS!', response.status, response.text);
    }, function(error) {
       console.log('FAILED...', error);
    });
  },
  isDisabled: function(){
    this.isActive ? this.isActive = false : this.isActive = true;
    this.isactivealert ? this.isactivealert = false : this.isactivealert = true;
  },
      calculate_kg: function(){
        // waga ceownika jest brana tylko ze stali czarnej!!
        this.suma_kg = Math.round(this.profil_konstrukcja_waga + this.szyna_kg + this.ceownik_kg + this.wyp_kg + this.slup1_kg + this.slup2_kg)
        // this.suma_kg = this.profil_konstrukcja_waga + this.szyna_kg + this.ceownik_kg + this.wyp_kg
      },
      // policz: function(){
      //    for(this.naped;this.naped<10000;this.naped++){
      //      return this.naped
      //     //  return this.usl1[i].cena
      //   }
      // },
      calculate_pln: function(){
        // this.uslugi_i_akcesoria_pln = 0
      // this.suma_pln = this.zebatki*100 + this.wozki*300 + this.naped*2000 + this.zabudowy*60 + this.kotwy*100 + this.antaba*200 + this.stopa*1500 + this.montaz*2500 + this.transport_do_klienta*200 + this.cynk_cena + this.lakier_cena + ((this.suma_kg * this.rodzaj_stali[this.rodzaj_stali_wybrane_id].cena_za_kg)*this.narzut)
      //

        this.suma_pln = Math.round(this.suma_akcesoria_pln*this.rodzaj_produktu[this.rodzaj_produktu_wybrane_id].narzut + this.transport_do_klienta*this.suma_kg + this.cynk_cena + this.lakier_cena + (this.montaz*(this.rodzaj_produktu[this.rodzaj_produktu_wybrane_id].montaz)) +((this.suma_kg * this.rodzaj_stali[this.rodzaj_stali_wybrane_id].cena_za_kg)*this.rodzaj_produktu[this.rodzaj_produktu_wybrane_id].narzut))
      },

      policz_akcesoria: function(){

      this.suma_akcesoria_pln = 0
      for (let i = 0; i < this.akcf.length; i++){
       this.suma_akcesoria_pln += this.akcesoria_furtka[this.akcf[i]].cena
         }

      },
      policz_akcesoria1: function(){

      this.suma_akcesoria_pln = 0
      for (let i = 0; i < this.akc_bprz.length; i++){
       this.suma_akcesoria_pln += this.akcesoria_bprz[this.akc_bprz[i]].cena
         }

      },
      policz_akcesoria2: function(){

      this.suma_akcesoria_pln = 0
      for (let i = 0; i < this.akc_bdw.length; i++){
       this.suma_akcesoria_pln += this.akcesoria_bdw[this.akc_bdw[i]].cena
         }

      },


    // ffeach: function(){

    //  if(this.usl1[1] == 0){return 100}

    // this.usl1.foreach((qqq) =>
    // {
    // return this.usl1[qqq]
    // }
    // )

    // Dlaczego nie wyświetla 10 razy i ani foreach ani for

    // for (let i = 0; i < 10; i){
    //   return this.usl1[i]
    // }

    // return Array.from(this.usl1).forEach(element => console.log(element)); // działa!!
    // },

      ustawiaj_opcje: function(){
      this.akcf = []
      this.akc_bprz = []
      this.akc_bdw = []
        if(this.rodzaj_produktu_wybrane_id == 0){
          this.akcf = [0,3,8,15,16]
          this.policz_akcesoria()
          this.pw = 0
          this.cdb = Math.round((this.swiatlo_bramy+this.pw)*100)/100
          this.obwod = Math.round((((this.swiatlo_bramy-0.08)*2 + (this.wys-0.08)*2))*100)/100
          this.obwodpw = 0
          this.swiatlo_bramy = 1
          this.rodzaj_stali_wybrane_id = 1
          this.szyna_mb = 0
          this.szyna_kg = 0
          this.calculate()
        }else if(this.rodzaj_produktu_wybrane_id == 1){
          this.akc_bprz = [0,6,7,8,11,12,13,14,16]
          this.policz_akcesoria1()
          this.swiatlo_bramy = 4
          this.pw = Math.round((this.swiatlo_bramy/3)*100)/100
          this.cdb = Math.round((this.swiatlo_bramy-+this.pw)*100)/100
          this.obwod = Math.round(((this.swiatlo_bramy*2 + (this.wys-0.16)*2))*100)/100
          this.obwodpw = Math.round((this.pw*3 + this.wys)*100)/100
          this.szyna_mb = this.swiatlo_bramy + this.pw
          this.szyna_kg = ((this.swiatlo_bramy + this.pw))*10
          this.swiatlo_bramy = 4
          this.calculate()
        }else if(this.rodzaj_produktu_wybrane_id == 2){
          this.akc_bdw = [0,5,6,7,8,11,14,16,18]
          this.policz_akcesoria2()
          this.swiatlo_bramy = 4
          this.pw = 0
          this.cdb = Math.round((this.swiatlo_bramy+this.pw)*100)/100
          this.obwod = Math.round((((this.swiatlo_bramy-0.08)*2 + (this.wys-0.08)*4))*100)/100
          this.obwodpw = 0
          this.szyna_mb = 0
          this.szyna_kg = 0
          this.calculate()
        }
      },

    }),
     computed: {
      cols () {
        const { lg, sm } = this.$vuetify.breakpoint
        return lg ? [3, 9] : sm ? [9, 3] : [6, 6]
      },


    },
}
</script>

<style lang="css">

.siteheader{
  margin:0 auto;
  margin-top:20px;
  margin-bottom:40px;
}

div .trzyde{
  width:100%;
  height:400px;
  margin-bottom:30px;
  margin-top:30px;
}

div .iconsfooter
{
  align-items: center;
  justify-content: center;
  vertical-align: middle;
  height:100%;
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