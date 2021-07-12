<template>
    <base-layout pageTitle="Todos los recuerdos">
        <ion-list>
            <ion-item router-link="/memories/1">Cerro Arco</ion-item>
            <ion-item>Encarnación</ion-item>
            <ion-item>Itaipú</ion-item>
            <ion-item>Barrero</ion-item>
        </ion-list>
    </base-layout>
</template>

<script>
import { IonList, IonItem } from '@ionic/vue'

export default {
    components:{
        IonList,
        IonItem
    }
}

</script>