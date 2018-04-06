<template>
  <form enctype="multipart/form-data" method="post " action="">
		<input @change="saveImage($event)" type="file" accept="image/*" capture>
		<img ref="preview" :src="src" />

		<div>
			<button type="submit">Upload Image</button>
		</div>
	</form>
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
    return { src: '' }
  },
  methods: {
    uploadToFirebase(file) {
    // Create a root reference
    const ref = firebase.storage().ref();
    const fileRef = ref.child(file.name);

    fileRef
      .put(file)
      .then(snapshot => {
        return fetch('https://pick-up-10-api-xodrwwxowz.now.sh/api?userid=welcome12345&url=' + snapshot.downloadURL)
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
