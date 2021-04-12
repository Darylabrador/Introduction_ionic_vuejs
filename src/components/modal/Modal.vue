<template>
  <ion-header>
    <ion-toolbar>
      <div style="display: flex">
        <ion-title>{{ title }}</ion-title>
        <ion-button small @click="closeDialog" :color="colorBtn"> X </ion-button>
      </div>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-content fullscreen>
      <ion-list>
        <ion-item v-for="datas in dataFromApp" :key="datas.title">
          <ion-label> {{ datas.color }} </ion-label>
          <ion-badge color="light" slot="end"> {{ datas.hex }} </ion-badge>
        </ion-item>
      </ion-list>
    </ion-content>
    {{ dataFromApp }}
  </ion-content>
</template>

<script>
import { IonContent, IonHeader, IonTitle, IonToolbar, IonButton, IonLabel, IonBadge, IonItem, IonList } from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Modal",
  components: { IonContent, IonHeader, IonTitle, IonToolbar, IonButton, IonLabel, IonBadge, IonItem, IonList },
  props: {
    dataFromApp: {
      type: Array,
    },
    title: {
      type: String,
      default: "Undefined",
    },
    colorBtn: {
        type: String
    }
  },

  methods: {
    closeDialog() {
      this.$emit("close", false);
    },
  },
});
</script>