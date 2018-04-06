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
    return { src: 'https://vuejs.org/images/logo.png' }
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
