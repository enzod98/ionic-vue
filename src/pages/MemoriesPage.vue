<template>
    <base-layout pageTitle="Todos los recuerdos">
        <ion-list>
            <ion-item 
            v-for="(memory, index) in memories" 
            :router-link="`/memories/${ memory.id }`"
            :key="index"
            >
            <ion-thumbnail slot="start">
                <ion-img :src="memory.img" :alt="memory.title"></ion-img>
            </ion-thumbnail>
            <ion-label>
                {{ memory.title }}
            </ion-label>
            </ion-item>
        </ion-list>
    </base-layout>
</template>

<script>
import { IonList, IonItem, IonImg, IonThumbnail, IonLabel } from '@ionic/vue'

export default {
    components:{
        IonList,
        IonItem,
        IonImg,
        IonThumbnail,
        IonLabel
    },
    data() {
        return {
            memories: [
                {
                    id: 'm1',
                    title: 'Cerro Arco',
                    description: 'Primer viaje con Sole',
                    img: 'https://arc-anglerfish-arc2-prod-abccolor.s3.amazonaws.com/public/4ETPJ7MRWZH4PJHQGATGHUWXVQ.jpg'
                },
                {
                    id: 'm2',
                    title: 'Encarnación',
                    description: 'El viaje más lejano en familia',
                    img: 'https://dynamic-media-cdn.tripadvisor.com/media/photo-o/05/68/71/3d/costanera-de-la-ciudad.jpg?w=700&h=500&s=1'
                },
                {
                    id: 'm3',
                    title: 'Itaipú',
                    description: 'Primer viaje con los panas en tercer grado',
                    img: 'https://upload.wikimedia.org/wikipedia/commons/b/b8/ItaipuAerea2AAL.jpg'
                },
                {
                    id: 'm4',
                    title: 'Barrero',
                    description: 'Locura y descontrol con los panas',
                    img: 'https://www.adndigital.com.py/wp-content/uploads/2017/08/eusebio-ayala-1.jpg'
                },
            ]
        }
    },
}

</script>