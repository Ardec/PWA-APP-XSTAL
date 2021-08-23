<template>

      <v-container
        fluid
      >
      <v-row class="headimg">
          <!-- <v-img src="../../src/assets/logo-cz.png" aspect-ratio="12" contain="true" class="mb-4 pt-4 mt10p"></v-img> -->
          <div class="herotext">
            <span class="herotop">OGRODZENIA</span>
            <span class="herobot">MATERIAŁY PRODUKCJA MONTAŻ</span>
            <!-- <span class="minitext">Hurtownia materiałów do budowy ogrodzeń </span> -->
          </div>
          <!-- <div class="sign-in-panel"><v-btn class="sign-in-btn" depressed outlined large>
      Zostań naszym partnerem
    </v-btn></div> -->
      </v-row>

      <v-row>
<v-parallax class="gates"
src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"

>


<v-row
      align="center"
      justify="center"
    >
      <v-col
        class="text-left"
        cols="6"
      >
        <h1 class="text-h4 font-weight-thin mb-4">
          Konfigurator bram i furtek
        </h1>
        <h4 class="subheading">
          Zaprojektuj swoją bramę
        </h4>
      </v-col>
      <v-col cols="3">
        <div class="gateconfig"></div>
      </v-col>


    </v-row>

</v-parallax>

      </v-row>



      </v-container>


</template>




<script>

export default {
  name: 'Home',
  components: {

  },
 data: () => ({

    }),

    methods: {
    }
}
</script>

<style lang="scss">


.center{
  text-align:center;
  font-weight: 300;
}
.mt10p{
  margin-top:10%
}
.sign-in-panel
{
  margin:0 auto;
  align-items: center;
  display:flex;
  justify-content: center;
  margin:20px 0px;
}

.gates
{
display:block;
width: 100%;
height: 850px;
}

.gateconfig{
background-image:url(../assets/bdw.png);
background-size: cover;
width:300px;
height:200px;
}


.headimg
{
  background-image: url("../assets/titleimg.jpg");
  background-size:cover;
  min-height:90vh;
  color:white;
  overflow: hidden;
}

.herotext
{
margin-top:10%
}

.herotop
{
  display:block;
  line-height:8rem;
  font-size: 6rem;
  margin-left:10%;
  font-weight: 600;
  letter-spacing: 0.3rem;
}

.herobot
{
  margin-top:1%;
  display:block;
  line-height: 3rem;
  font-size: 3rem;
  margin-left:10%;
  font-weight: 300;
  letter-spacing: 0.3rem;
  word-spacing: 0.6rem;
}

.minitext{
  display:block;
  margin-left:10%;
}

@media screen and (max-width: 700px){

.herotop
{
  display:block;
  line-height:3.5rem;
  font-size: 2.5rem;
  font-weight: 600;
  margin-left:5%;
  letter-spacing: 0.25rem;
  text-align: left;
}
.herobot
{
  display:block;
  line-height: 1.3rem;
  font-size: 1.1rem;
  margin-left:5%;
  font-weight: 300;
  letter-spacing: 0.3rem;
  word-spacing: 0.6rem;
}
.herotext
{
display:block;
max-width:100%;
margin:20% auto;
}
}

</style>