<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Mes couleurs</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Mes couleurs</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <ion-button @click="openBlueModal(true)"> Les teintes bleu </ion-button>
        <ion-button color="warning" @click="openYellowModal(true)"
          >Les teintes jaune
        </ion-button>
        <ion-button color="success" @click="openGreenModal(true)"
          >Les teintes verte
        </ion-button>
      </div>

      <ion-modal :is-open="blueModal" @onDidDismiss="closeModal(false)">
        <Modal
          @close="closeModal"
          :title="titleData"
          :dataFromApp="dataFromApp"
          :colorBtn="colorBtn"
        ></Modal>
      </ion-modal>

      <ion-modal :is-open="yellowModal" @onDidDismiss="closeModal(false)">
        <Modal
          @close="closeModal"
          :title="titleData"
          :dataFromApp="dataFromApp"
          :colorBtn="colorBtn"
        ></Modal>
      </ion-modal>

      <ion-modal :is-open="greenModal" @onDidDismiss="closeModal(false)">
        <Modal
          @close="closeModal"
          :title="titleData"
          :dataFromApp="dataFromApp"
          :colorBtn="colorBtn"
        ></Modal>
      </ion-modal>
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
  IonButton,
  IonModal,
} from "@ionic/vue";
import Modal from "@/components/modal/Modal.vue";

export default {
  name: "Tab2",
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    Modal,
    IonButton,
    IonModal,
  },
  data() {
    return {
      blueModal: false,
      yellowModal: false,
      greenModal: false,
      titleData: "",
      dataFromApp: [],
      colorBtn: "",
    };
  },
  methods: {
    closeModal(isOpen) {
      this.blueModal = isOpen;
      this.yellowModal = isOpen;
      this.greenModal = isOpen;
      this.titleData = "";
      this.colorBtn = "";
      this.dataFromApp = [];
    },
    openBlueModal(isOpen) {
      this.blueModal = isOpen;
      this.colorBtn = "primary";
      this.titleData = "Nuances de bleu";
      this.dataFromApp.push(
        {
          color: "Cyan",
          hex: "#00BCD4",
        },
        {
          color: "Indigo",
          hex: "#3F51B5",
        }
      );
    },
    openYellowModal(isOpen) {
      this.yellowModal = isOpen;
      this.titleData = "Nuances de jaune";
      this.colorBtn = "warning";
      this.dataFromApp.push(
        {
          color: "Jaune",
          hex: "#FFEB3B",
        },
        {
          color: "Jaune foncé",
          hex: "#FBC02D",
        }
      );
    },
    openGreenModal(isOpen) {
      this.greenModal = isOpen;
      this.titleData = "Nuances de vert";
      this.colorBtn = "success";
      this.dataFromApp.push(
        {
          color: "Vert",
          hex: "#4CAF50",
        },
        {
          color: "Vert pomme",
          hex: "#66BB6A",
        }
      );
    },
  },
};
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}
</style>