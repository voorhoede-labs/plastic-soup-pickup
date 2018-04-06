<template>
  <div class="get-ready">
    <img src="~/assets/get-ready/get-ready-bg.png" class="get-ready-bg" />

    <div class="get-ready-content">
      <h1 class="photo-title">GET READY <span class="photo-subtitle">to pick up 10</span></h1>
      <img src="~/assets/get-ready/get-ready-mobile.png" class="get-ready-mobile" />
      <p class="photo-text">Photograph the plastic horizontally and include the brand name</p>

      <form class="photo-form" enctype="multipart/form-data" method="post " action="">
        <input id="browse-photos" type="file" class="input-browse-photos">
        <label class="label-browse" for="browse-photos">
          <span>camera</span>
        </label>

        <input @change="saveImage($event)" id="take-photo" type="file" class="input-take-photo" accept="image/*" capture>
        <label class="label-take" for="take-photo">
          <span>photo</span>
        </label>
    </form>
    </div>

    <img ref="preview" :src="src" class="image-preview" />
  </div>
</template>

<script>
import firebase from 'firebase';

try {
  firebase.initializeApp({
    apiKey: "AIzaSyCTVK7d719KT2-ylcUAGZ4x0SY0Pc1nuVY",
  			authDomain: "pick-up-10-2e988.firebaseapp.com",
  			databaseURL: "https://pick-up-10-2e988.firebaseio.com",
  			projectId: "pick-up-10-2e988",
  			storageBucket: "gs://pick-up-10-2e988.appspot.com",
  			messagingSenderId: "317354700389"
  });
} catch (err) {
  console.log('Firebase already initialized');
}

export default {
  data() {
    return {
      src: ''
    }
  },
  methods: {
    uploadToFirebase(file) {
    // Create a root reference
    const ref = firebase.storage().ref();
    const fileRef = ref.child(file.name);

    fileRef
      .put(file)
      .then(snapshot => {
        return fetch('https://pick-up-10-api-wshddsgbes.now.sh/api?userid=welcome12345&imageurl=' + snapshot.downloadURL)
      })
      .then(res => res.json())
      .then(this.getLabels)
      .then(console.log)
      .catch(alert);
    },
    saveImage({ target }) {
      const input = target;
      if (input.files && input.files[0]) {
        const reader = new FileReader();
        const file = input.files[0];

        reader.onload = event => {
          this.src = event.target.result;
        };
        reader.readAsDataURL(file);
        this.uploadToFirebase(file);
      }
    },
    getLabels(recognition) {
      const bestGuesses = recognition.webDetection.bestGuessLabels;
      const entities = recognition.webDetection.webEntities
        .filter(entity => entity.score > .6);

      return {
        bestGuess: bestGuesses[0],
        entities
      }
    }
  }
}
</script>

<style>
.get-ready {
  position: relative;
  height: 100vh;
}

.get-ready-bg {
  position: absolute;
  z-index: 1;
  max-width: 100%;
  height: auto;
}

.get-ready-content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 40px;
  height: 70vh;
  align-items: center;
  padding-left: 24px;
  padding-right: 24px;
}

.get-ready-mobile {
  margin-top: 15px;
  z-index: 2;
  max-width: 60%;
  height: auto;
}

.image-preview {
  max-width: 100%;
  height: auto;
}

.input-browse-photos,
.input-take-photo {
  width: 0.1px;
  height: 0.1px;
  opacity: 0;
  overflow: hidden;
  position: absolute;
  z-index: -1;
}

.photo-form {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  width: 80%;
  margin-top: 76px;
}

.photo-title {
  z-index: 2;
  color: #fff;
  text-align: center;
}

.photo-subtitle {
  display: block;
  margin-top: -10px;
  font-size: 24px;
  text-transform: uppercase;
}

.photo-text {
  z-index: 5;
  text-align: center;
  color: #fff;
}

.label-browse,
.label-take {
  position: relative;
  z-index: 4;
  display: inline-block;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  padding: 20px;
  background-color: #f0706c;
}

.label-browse span,
.label-take span {
  position: absolute;
  top: 100%;
  text-align: center;
  left: 0;
  width: 100%;
}


</style>
