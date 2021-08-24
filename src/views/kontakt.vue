<template>
  <div class="container">
 <div class="contact pt-8">
      <h1>Informacje kontaktowe</h1><br>
      <h4>Skład budowlany:</h4>
      <!-- <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Beatae reprehenderit officiis at minus vitae odit sed inventore, pariatur veniam dolorem autem exercitationem hic necessitatibus, magnam libero, corporis porro! Consequatur, nihil.</p>
      <h4>Dane punktu handlowego w Trzebini</h4> -->
      <p>  Xstal - Grupa Modernbau <br> 32-540 Trzebinia <br> ul. Długa 51  <br>
      Poniedziałek - Piątek 7:00 - 17.00  <br> Sobota 7.00 - 13.00 <br> tel. 730-310-025 <br> biuromodernbau@gmail.com <br>
      </p>
      <h4>Dane spółki:</h4>
      <p>
        Technology Farm spółka z ograniczoną odpowiedzialnością <br>
        30-017 Kraków, ul. Racławicka 58 <br>
         NIP: 5170368405 <br>
        </p>
        <h4>Kontakt telefoniczny:</h4>
        <p>
        Kamil Kaczmarczyk - 508786884<br>
        </p>
 </div>
   </div>
</template>

<script>
  import { validationMixin } from 'vuelidate'
  import { required, maxLength, email } from 'vuelidate/lib/validators'

  export default {
    mixins: [validationMixin],

    validations: {
      name: { required, maxLength: maxLength(10) },
      email: { required, email },
      select: { required },
      checkbox: {
        checked (val) {
          return val
        },
      },
    },

    data: () => ({
      name: '',
      email: '',
      select: null,
      items: [
        'Wycena Ogrodzeń',
        'Wycena Stali',
      ],
      checkbox: false,
    }),

    computed: {
      checkboxErrors () {
        const errors = []
        if (!this.$v.checkbox.$dirty) return errors
        !this.$v.checkbox.checked && errors.push('You must agree to continue!')
        return errors
      },
      selectErrors () {
        const errors = []
        if (!this.$v.select.$dirty) return errors
        !this.$v.select.required && errors.push('Item is required')
        return errors
      },
      nameErrors () {
        const errors = []
        if (!this.$v.name.$dirty) return errors
        !this.$v.name.maxLength && errors.push('Name must be at most 10 characters long')
        !this.$v.name.required && errors.push('Name is required.')
        return errors
      },
      emailErrors () {
        const errors = []
        if (!this.$v.email.$dirty) return errors
        !this.$v.email.email && errors.push('Must be valid e-mail')
        !this.$v.email.required && errors.push('E-mail is required')
        return errors
      },
    },

    methods: {
      submit () {
        this.$v.$touch()
      },
      clear () {
        this.$v.$reset()
        this.name = ''
        this.email = ''
        this.select = null
        this.checkbox = false
      },
    },
  }
</script>

<style lang="scss">

h1 {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-weight:500;
}

p {
// border-left: solid red 2px;
// padding-left: 10px;
}
</style>