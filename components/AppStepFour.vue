<template>
	<div class="app-step">
		<h2 class="header-subtitle">EACH DROP MAKES THE OCEAN</h2>
		<div class="text-container">
      <p>Recognition of the litter that way we know which companies are the source ask them to take more action & responsibly make other people aware - be a role model more than picking up litter - not only cleaning but also monitoring, get the data, power our voices towards companies, and have them be more responsible.</p>
		</div>
    <engage-button class="action" />
	</div>
</template>

<style>
.action {
  margin-top: 60px;
}

.text-container {
  line-height: 1.4rem;
}

.app-step {
	margin-bottom: 40px;
}

.app-step-text {
	margin-bottom: 20px;
}

.header {
	width: 100%;
	display: flex;
	height: 60px;
	margin-bottom: 10px;
}

.header-title {
	width: 85%;
	font-size: 2.5rem;
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

</style>

<script>
import EngageButton from '~/components/EngageButton.vue'

  export default {
    components: {
      EngageButton,
    }
  }
</script>

