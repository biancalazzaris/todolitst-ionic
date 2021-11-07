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
              <ion-label position="floating">Nome do seu pet</ion-label>
              <ion-input type="text" v-model="pet.nome"></ion-input>
            </ion-item>
            <ion-item class="item">
              <ion-label position="floating">Idade do seu pet</ion-label>
              <ion-input type="number" v-model="pet.idade"></ion-input>
            </ion-item>
            <ion-button
              class="btn"
              expand="block"
              color="success"
              v-on:click="salvarPet(pet)"
              >Salvar</ion-button
            >
          </ion-col>
        </div>
      </div>
    </ion-content>
    <ion-item v-for="(petstorage, index) in pets" :key="index">
      <ion-card>
        <ion-card-header>
          <ion-card-title> Nome do pet: {{ petstorage.nome }}</ion-card-title>
          <ion-card-subtitle
            >Idade: {{ petstorage.idade }} anos</ion-card-subtitle
          >
        </ion-card-header>
      </ion-card>
    </ion-item>
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
  IonCard,
  IonCardHeader,
  IonCardSubtitle,
  IonCardTitle,
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
    IonCard,
    IonCardHeader,
    IonCardSubtitle,
    IonCardTitle,
  },

  data() {
    return {
      pets: [],
      pet: {
        nome: "",
        idade: "",
      },
    };
  },
  created() {
    this.pets = JSON.parse(localStorage.getItem("petstorage"));
  },
  methods: {
    salvarPet(pet) {
      let pets = localStorage.getItem("petstorage");

      if (pets) {
        pets = JSON.parse(pets);
        pets.push(pet);
      } else {
        pets = [pet];
      }
      this.pets = pets;
      localStorage.setItem("petstorage", JSON.stringify(pets));
    },
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