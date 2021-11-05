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
              v-model="namePet"></ion-input>
            </ion-item>
            <ion-item class="item">
              <ion-label position="floating">Age</ion-label>
              <ion-input 
              type="number" 
              v-model="agePet"></ion-input>
            </ion-item>
            <ion-button class="btn" expand="block" color="success" @click="salvarInformacoes">Salvar</ion-button>
            <h6>Nome: {{ Name }} | Idade: {{ agePet }} </h6>
          </ion-col>
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
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
  name: "Tab2",
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
    salvarInformacoes() {
      const Name = this.namePet;
      this.Name = Name;
      const Age = this.agePet;
      this.Age = Age;
    },
  },
  data() {
    return {
      namePet: "",
      Name: "",
      Age: "",
      agePet: ""
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