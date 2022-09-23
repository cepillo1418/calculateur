<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 3</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 3</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-item>
        <ion-label position="floating">Code département</ion-label>
        <ion-input type="number" v-model="codeDepartment"></ion-input>
      </ion-item>
      <ion-button color="primary" @click="getCities">Chercher</ion-button>

      <div id="list__cities">
        <div v-for="(city, index) in arrayCities" :key="index">
          <h1>Nom: {{ city.nom }}</h1>
          <p>Code postal: {{ city.codesPostaux[0] }}</p>
          <p>Population: {{ city.population }}</p>
        </div>
      </div>

    </ion-content>
  </ion-page>
</template>

<script>
import {defineComponent, ref} from 'vue';
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonInput, IonButton, IonItem, IonLabel } from '@ionic/vue';
import {HTTP} from '@awesome-cordova-plugins/http'

export default defineComponent({
  name: 'Tab3Page',
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonInput, IonButton, IonItem, IonLabel },
  setup() {
    let codeDepartment = ref()
    let arrayCities = ref()

    const getCities = () => {
      HTTP.get(`https://geo.api.gouv.fr/communes?codePostal=${codeDepartment.value}&fields=nom,code,codesPostaux,siren,codeEpci,codeDepartement,codeRegion,population&format=json&geometry=centre`, {}, {})
          .then(response => {
            arrayCities.value = JSON.parse(response.data)
            console.log(response.status)
            console.log(JSON.parse(response.data)[0].nom) // data received by server
            console.log(response.headers)
          })
          .catch(error => {
            console.log(error.status)
            console.log(error.error) // error message as string
            console.log(error.headers)
          })
    }

    return {codeDepartment, arrayCities, getCities}
  }
});
</script>

<style scoped>
#list__cities div {
  padding: 10px;
  background: #d4d4d4;
  border-radius: 8px;
  margin: 5px;
  color: #282828
}
</style>


