<template>
	<div class="app-step">
		<div class="header">
			<h1 class="header-title">#PICKUP 10</h1>
			<div class="image-logo"></div>
		</div>
		<h2 class="header-subtitle">PLASTIC DATA IS POWER</h2>
		<div class="full-width-video"></div>
		<div class="text-container">
			<p>There is too much plastic in the world that ends up in the oceans. This is not only bad for the environment, but also the marine life and us, the human beings. We can tackle this plastic issue at the source by creating a real database of the plastic debris. By registering the existing plastic waste, we bring the power back in the citizens hands and hold the companies accountable.</p>
		</div>
	</div>
</template>

<style>
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
	margin-bottom: 10px;
}

</style>
