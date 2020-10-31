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

      <ion-slides style="height: 50px;" pager="false" :options="slideOpts">
        <ion-slide>
          <div style="display: flex;width:100%">
            <ion-button style="flex:1" v-for="(elem,$index) in ['M','T','W','T','F','S','S']"
              :key="$index" @click="activate($index)" :color="days[$index]?'success':''">{{ elem }}</ion-button>
          </div>
        </ion-slide>
      </ion-slides>
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
  IonSlides,
  IonSlide,
  IonButton
} from '@ionic/vue'
import { reactive } from 'vue'
export default {
  name: 'Tab1',
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonSlides,
    IonSlide,
    IonButton
  },
  setup() {
    const days = reactive([true, false, false, false, false, false, false])
    const activate = (day) => {
      alert("clicked")
      console.log("should activate day",day)
      for (let i=0;i<days.length;i++){
        if (i==day) days[i]=true
        else days[i]=false
      }
    }
    const slideOpts = {
      initialSlide: 1,
      speed: 400,
      loop: true,
    }
    return {
      slideOpts,
      days,
      activate
    }
  },
}
</script>

<style>
.active {
  font-weight: bold;
}
</style>
