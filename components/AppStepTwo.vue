<template>
	<div class="app-step">
		<h2 class="header-subtitle">RISE UP, PICK UP, BACK UP</h2>
		<p class="app-step-text">Pick 10 plastic bottles citizens can create a new feedback system for companies back in up on the system.</p>
		<ul class="list">
			<li class="list-item">
				<div class="list-item-image"></div>
				<div class="list-item-text">
					<span class="h2">1.</span>
					<span>Rise up and go outside</span>
				</div>
			</li>
			<li class="list-item">
				<div class="list-item-image"></div>
				<div class="list-item-text">
					<span class="h2">2.</span>
					<span>Pick up 10 plastics </span>
				</div>
			</li>
			<li class="list-item">
				<div class="list-item-image"></div>
				<div class="list-item-text">
					<span class="h2">3.</span>
					<span>flaksjdf</span>
				</div>
			</li>
			<li class="list-item-center">
				<engage-button />
			</li>
		</ul>
		<div class="divider-layer-one"></div>
	</div>
</template>

<script>
import EngageButton from '~/components/EngageButton.vue'

export default {
  components: {
    EngageButton,
  }
}
</script>


<style>
.list-item-center {
	display: flex;
	align-items: center;
	justify-content: center;
	width: 100%;
}

.divider-layer-one {
	background-image: url(https://plasticsoupsurfer.org/assets/icons/expedition-wave.svg);
    background-size: cover;
    background-repeat: no-repeat;
    width: 110%;
    height: 115px;
    left: -10px;
    position: relative;
}

.list {
	display:flex;
	flex-direction: column;
}
.list-item {
	display: flex;
	margin-bottom: 20px;
}
.list-item-text {
	display: flex;
	flex-direction: column;
	justify-content: center;
}
.list-item-image {
	width: 40%;
    background-image: url(https://plasticsoupsurfer.org/assets/images/logo.png);
    background-size: contain;
    background-repeat: no-repeat;
    height: 140px;
}
.header {
	width: 100%;
	display: flex;
	height: 60px;
}

.header-title {
	width: 85%;
	color: #2B2F47;
	text-align: center;
	display: flex;
    justify-content: flex-start;
    align-items: center;
}
.header-subtitle {
	text-transform: uppercase;
	align-items: center;
	display: flex;
	color: #F26F69;
	margin-bottom: 10px;
}
.image-logo {
	width: 15%;
	background-image: url(https://plasticsoupsurfer.org/assets/images/logo.png);
	background-size: contain;
    background-position: center center;
	background-repeat: no-repeat;
}
.full-width-video {
	position: relative;
	display: flex;
	width: 100%;
	height: 65vh;
	background: grey;
	background-image: url(https://plasticsoupsurfer.org/assets/images/header-s.jpg);
	background-size: cover;
    background-position: center;
	background-repeat: no-repeat;
	align-items: flex-end;
	justify-content: center;
	margin-bottom: 20px;
}

</style>
