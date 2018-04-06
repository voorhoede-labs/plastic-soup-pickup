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
import firebase from 'firebase'
const app = firebase.initializeApp({
  apiKey: "AIzaSyCTVK7d719KT2-ylcUAGZ4x0SY0Pc1nuVY",
			authDomain: "pick-up-10-2e988.firebaseapp.com",
			databaseURL: "https://pick-up-10-2e988.firebaseio.com",
			projectId: "pick-up-10-2e988",
			storageBucket: "gs://pick-up-10-2e988.appspot.com",
			messagingSenderId: "317354700389"
});

export default {
  data() {
    return { src: 'https://vuejs.org/images/logo.png' }
  },
  methods: {
    saveImage({ target }) {
      const input = target;
      if (input.files && input.files[0]) {
        const reader = new FileReader();
        const file = input.files[0];

        reader.onload = event => {
          this.src = event.target.result;
        };

        reader.readAsDataURL(file);

        // uploadToFirebase(file);

        // fetch("http://www.example.net", {
        //   method: "POST",
        //   body: file
        // }).then(response => response.json());
      }
    }
  }
}
</script>

