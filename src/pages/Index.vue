<template>

 <!-- <q-page>
    <router-link to="/Exercice1" exact-active-class="actif">Exercice1</router-link>
    <div>Je suis une <strong>div</strong></div>
    <p>Je suis un parapgraphe</p>
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-full.svg"
    >
  </q-page> -->

  <q-page padding>
    <div class="form q-mb-lg">
      <div class="row q-mb-md">
        <label>Nom:</label>
        <input v-bind:class="(nom.length > 15)?'error':''" v-model="nom" type="text">
        <label class="error" v-show="nom.length > 15">Maximum 15 caractères
        </label>
      </div>
      <div class="row q-mb-md">
        <label>Age:</label>
        <input ref="fnom" v-bind:class="(parseInt(age) < 1 || parseInt(age) > 100)?'error':''" v-model="age" type="number">
        <label class="error" v-show="parseInt(age) < 1 || parseInt(age)>100">Veuillez entrer un âge compris entre 1 et 100</label>
      </div>
      <div class="row">
        <button v-on:click="generate">Générer une personne</button>
      </div>
    </div>
    <div class="description q-mb-lg" v-show="nom.length < 16 && parseInt(age) <= 100 && parseInt(age) > 0">
      <p>Mon nom est <b>{{ nom }}</b> et j'ai <b>{{ age }}</b> ans.</p>
      <p>Dans 10 ans, j'aurai <b>{{ parseInt(age) + 10 }}</b> ans.</p>
      <p>Mon nom se compose de <b>{{ nom.length }}</b> caractères.</p>
      <p>Mon nom en majuscules est <b>{{ nomUpperCase }}</b>.</p>
    </div>
    <div class="no-details" v-show="parseInt(age) > 100 || nom.length > 15">
      <p >Veuillez entrer un nom et un âge valide !</p>
    </div>
  </q-page>
</template>

<script>

const TableauNom = ['Robert', 'Nicole', 'Paul', 'Françoise']

function entierAleatoire (min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min
}
// Déclaration du composant Vue
export default {
  name: 'Exercice1',
  data () {
    return {
      nom: '',
      age: '',
      hasError: '',
      monTableau: [
        { prenom: 'click' },
        { prenom: 'clack' }
      ]
    }
  },
  computed: {
    nomUpperCase () {
      console.log('nomUpperCase')
      return this.nom.toUpperCase()
    }
  },
  mounted () {
    this.focusInput()
    this.generate()
  },
  methods: {
    generate: function (event) {
      this.nom = TableauNom[entierAleatoire(0, 3)]
      this.age = entierAleatoire(1, 100)
    },
    focusInput () {
      this.$refs.fnom.focus()
    }
  }
}
</script>
<style>
.form {
  background: #eee;
  padding: 10px;
}
label {
  min-width: 70px;
}
label.error {
  font-size: 13px;
  color: red;
  margin-left: 5px;
  margin-top: 3px;
}
input {
  border: 1px solid #ccc;
}
input.error {
  border: 1px solid red;
  background: pink;
}
.description {
  background: antiquewhite;
  padding: 20px 20px 7px;
}
.no-details {
  background: lightcoral;
  padding: 20px 20px 7px;
}
</style>
