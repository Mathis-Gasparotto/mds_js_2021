<template>
  <form v-on:submit.prevent="onSubmit" v-if="step === '1'">
    <Title :style="{color:colorie}" title="Identité de base"/>
    <div class="row">
      <TextInput name="name" label="Prénom : "/>
      <TextInput name="lastname" label="Nom : "/>
    </div>
    <div>
      <DateInput name="birthday" label="Date de naissance : "/>
    </div>
    <div>
      <BtnForm type="submit" text="Suivant" v-on:validation="colorie='green'" v-on:step="step='2'" />
    </div>
    <div>
      <BtnForm type="reset" text="Réinitialiser" v-on:validation="colorie='red'" />
      <BtnRefresh txt="Rafraichir" />
    </div>
    <div>
      <SelectColor name="color" label="Choisissez la couleur du titre : " v-on:blue="colorie='blue'" v-on:white="colorie='white'" v-on:red="colorie='red'" />
    </div>
    <div>
      <BtnColor text="Bleu" v-on:color="colorie='blue'" />
      <BtnColor text="Blanc" v-on:color="colorie='white'" />
      <BtnColor text="Rouge" v-on:color="colorie='red'" />
    </div>
    <div>
      <FormMsg msg="Envoie réussi" colorie="green" />
      <FormMsg msg="Envoie échoué" colorie="red" />
    </div>
  </form>

  <form v-on:submit.prevent="onSubmit" v-if="step === '2'">
    <Title :style="{color:colorie}" title="Message"/>
    <div>
      <TextArea name="message" label="Message : " col="30" row="10" />
    </div>
    <div>
      <BtnForm type="submit" text="Suivant" v-on:validation="colorie='green'" v-on:step="step='3'" />
      <BtnStep text="Retour en arrière" v-on:step="step='1'" />
    </div>
    <div>
      <BtnForm type="reset" text="Réinitialiser" v-on:validation="colorie='red'" />
      <BtnRefresh txt="Rafraichir" />
    </div>
    <div>
      <FormMsg msg="Envoie réussi" colorie="green" />
      <FormMsg msg="Envoie échoué" colorie="red" />
    </div>
  </form>

  <form v-on:submit.prevent="onSubmit" v-if="step === '3'">
    <Title :style="{color:colorie}" title="Identité avancée"/>
    <div>
      <Select name="profession" label="Profession : " />
    </div>
    <div>
      <RadioBtn name="sex" label="Sex : " />
    </div>
    <div>
      <Checkbox label="Compétence(s) : " />
    </div>
    <div>
      <BtnForm type="submit" text="Valider" v-on:validation="colorie='green'" />
      <BtnStep text="Retour en arrière" v-on:step="step='2'" />
      <BtnStep text="Retour au début" v-on:step="step='1'" />
    </div>
    <div>
      <BtnForm type="reset" text="Réinitialiser" v-on:validation="colorie='red'" />
      <BtnRefresh txt="Rafraichir" />
    </div>
    <div>
      <FormMsg msg="Envoie réussi" colorie="green" />
      <FormMsg msg="Envoie échoué" colorie="red" />
    </div>
  </form>
  


</template>

<script>
import Title from './components/Title.vue'
import TextInput from './components/TextInput.vue'
import DateInput from './components/DateInput.vue'
import TextArea from './components/TextArea.vue'
import Select from './components/Select.vue'
import RadioBtn from './components/RadioBtn.vue'
import Checkbox from './components/Checkbox.vue'
import BtnForm from './components/BtnForm.vue'
import FormMsg from './components/FormMsg.vue'
import BtnStep from './components/BtnStep.vue'
import BtnRefresh from './components/BtnRefresh.vue'
import SelectColor from './components/SelectColor.vue'
import BtnColor from './components/BtnColor.vue'

export default {
  name: 'App',
  components: {
    Title,
    TextInput,
    DateInput,
    TextArea,
    Select,
    RadioBtn,
    Checkbox,
    BtnForm,
    FormMsg,
    BtnStep,
    BtnRefresh,
    SelectColor,
    BtnColor
  },
  data() {
    return {
      colorie: '#2c3e50',
      step: '1'
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
template{
  flex-direction: column;
  justify-content: center;
}
.row {
  flex-direction: row;
}
</style>
