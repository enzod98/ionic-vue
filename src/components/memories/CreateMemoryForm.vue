<template>
  <form class="ion-padding" @submit.prevent="submitForm">
    <ion-list>
      <ion-item>
        <ion-label position="floating">Título</ion-label>
        <ion-input type="text" required v-model="title" />
      </ion-item>
      <ion-item>
        <ion-thumbnail slot="start">
          <img :src="previewImgUrl" />
        </ion-thumbnail>
        <ion-button type="button" fill="clear" @click="takePhoto">
          <ion-icon slot="start" :icon="camera" ></ion-icon>
          Take Photo
        </ion-button>
      </ion-item>
      <ion-item>
        <ion-label position="floating">Descripción</ion-label>
        <ion-textarea rows="5" v-model="description" />
      </ion-item>
    </ion-list>
    <ion-button type="submit" expand="block">Añadir</ion-button>
  </form>
</template>

<script>
import {
  IonList,
  IonItem,
  IonLabel,
  IonInput,
  IonTextarea,
  IonButton,
  IonThumbnail,
  IonIcon
} from "@ionic/vue";

import { camera } from 'ionicons/icons'
import { Camera, CameraResultType } from '@capacitor/camera';


export default {
  emits: ['save-memory'],
  components: {
    IonList,
    IonItem,
    IonLabel,
    IonInput,
    IonTextarea,
    IonButton,
    IonThumbnail,
    IonIcon
  },
  data() {
      return {
          title: '',
          imgUrl: '',
          description: '',
          camera,
          previewImgUrl: null
      }
  },
  methods: {
      submitForm(){
          const memoryData = {
              title: this.title,
              imgUrl: this.imgUrl,
              description: this.description
          }

          this.$emit('save-memory', memoryData);
      },
      async takePhoto(){
        let photo = await Camera.getPhoto({
          resultType: CameraResultType.Uri, //Quiere decir que la foto se guardará en un almacenamiento temporal del dispositivo y obtenemos una URI que apunta a esa dirección
          quality: 100 //Calidad de la imagen en porcentajes
        });

        this.previewImgUrl = photo.webPath;
      }
  }
};
</script>
