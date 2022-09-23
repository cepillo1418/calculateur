<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-item>
        <ion-label position="floating">Ajouter une partie</ion-label>
        <ion-input type="text" v-model="partie"></ion-input>
      </ion-item>
      <ion-button type="submit" color="medium" @click="addPartie">Ajouter</ion-button>

    
    </ion-content>
  </ion-page>
</template>

<script>

</script>

