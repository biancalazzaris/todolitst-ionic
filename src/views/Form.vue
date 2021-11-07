<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>PET DB</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <div class="container">
        <div>
          <ion-col>
            <ion-item class="item">
              <ion-label position="floating">Name pet</ion-label>
              <ion-input 
              type="text" 
              v-model="pet.nome"></ion-input>
            </ion-item>
            <ion-item class="item">
              <ion-label position="floating">Age</ion-label>
              <ion-input 
              type="number" 
              v-model="pet.idade"></ion-input>
            </ion-item>
            <ion-button class="btn" expand="block" color="success" v-on:click="salvarPet(pet)">Salvar</ion-button>
          </ion-col>
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonCol,
  IonItem,
  IonLabel,
  IonInput,
  IonButton,
} from "@ionic/vue";
import { defineComponent } from "vue";
export default defineComponent({
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonCol,
    IonItem,
    IonLabel,
    IonInput,
    IonButton,
  },
  methods: {
      salvarPet(pet){
          let pets = localStorage.getItem('petstorage');

          if(pets) {
              pets = JSON.parse(pets);
              pets.push(pet);
          }else{
              pets = [pet];
          }

          localStorage.setItem('petstorage', JSON.stringify(pets))
      }
  },
  data() {
    return {
        pet: 
            {
                nome: '',
                idade: ''
            },
    };
  },
});
</script>


 
<style scoped>
.container {
    display: flex;
    justify-content: center;
}
.btn {
    margin: 30px 20px;
}
</style>