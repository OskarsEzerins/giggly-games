<script lang="ts">
	import { goto } from '$app/navigation';

	function playNow() {
		goto('/triple-word-flickster');
	}
</script>

<div class="hero">
	<h1 class="hero-title">Welcome to Giggly Games!</h1>
	<p class="hero-description">
		Experience endless fun and excitement with Giggly Games! Our platform offers a wide variety of
		quick, engaging games that will keep you entertained for hours. Jump in and start playing!
	</p>
	<button class="play-btn" on:click={playNow}>Play Now</button>
</div>

<!-- <div class="games-section">
	<div class="game-card">Game 1</div>
</div> -->
<style>
	.hero {
		font-family: 'Roboto', sans-serif;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100vh;
		background-color: #f1c40f;
		color: #2c3e50;
		flex-direction: column;
	}

	.hero-title {
		font-size: 3rem;
		font-weight: bold;
		margin: 5vh;
	}

	.hero-description {
		font-size: 1.2rem;
		text-align: center;
		max-width: 800px;
		margin: 0 auto 20px;
		line-height: 1.5;
	}

	.play-btn {
		padding: 12px 24px;
		background-color: #2c3e50;
		color: #fff;
		border: none;
		border-radius: 4px;
		font-size: 1.2rem;
		cursor: pointer;
		transition: all 0.3s ease;
	}

	.play-btn:hover {
		background-color: #34495e;
	}

	.games-section {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		padding: 20px;
		background-color: #2c3e50;
	}

	.game-card {
		width: 200px;
		height: 200px;
		background-color: #f1c40f;
		border-radius: 8px;
		margin: 20px;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 1.5rem;
		font-weight: bold;
		color: #2c3e50;
		transition: all 0.3s ease;
	}

	.game-card:hover {
		transform: scale(1.05);
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.15);
	}
</style>
