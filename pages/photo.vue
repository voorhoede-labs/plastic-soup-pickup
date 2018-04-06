<template>
  <div>
    <img ref="preview" :src="src" class="image-preview" />

    <h1>GET READY <span class="photo-subtitle">to pick up 10</span></h1>

    <p></p>

    <form enctype="multipart/form-data" method="post " action="">
      <input id="browse-photos" type="file" class="input-browse-photos">
      <label for="browse-photos">camera</label>
      <input @change="saveImage($event)" id="take-photo" type="file" class="input-take-photo" accept="image/*" capture>
      <label for="take-photo">photo</label>
    </form>
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
      .then(this.getLabel)
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
    getLabel(recognition) {
      const bestGuesses = recognition.webDetection.bestGuessLabels;
      return bestGuesses.length ? bestGuesses[0].label : 'No product recognized'
    }
  }
}
</script>

<style>
.image-preview {
  max-width: 100%;
  height: auto;
}

.input-browse-photos,
.input-take-photo {
  width: 0.1px;
  height: 0.1;
  opacity: 0;
  overflow: hidden;
  position: absolute;
  z-index: -1;
}
</style>
