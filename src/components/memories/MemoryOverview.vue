<template>
  <ion-img :src="img" :alt="title" />
  <h2 class="ion-text-center">{{ title }}</h2>
  <p class="ion-text-center">{{ description }}</p>
</template>

<script>
import { IonImg } from '@ionic/vue'
export default {
    props: ["title", "img", "description"],
    components:{
        IonImg
    }
}
</script>