<script lang="ts">
	import { goto } from '$app/navigation';

	function playNow() {
		goto('/triple-word-flickster');
	}
</script>

<div class="hero">
	<h1 class="hero-title">
		<div class="title-word title-word-1">Welcome</div>
		<div class="title-word title-word-2">to</div>
		<div class="title-word title-word-3">Giggly</div>
		<div class="title-word title-word-4">Games!</div>
	</h1>
	<p class="hero-description">
		Experience endless fun and excitement with Giggly Games! Our platform offers a wide variety of
		quick, engaging games that will keep you entertained for hours.
	</p>
	<button class="play-btn" on:click={playNow}>Jump in and start playing!</button>
</div>

<!-- <div class="games-section">
	<div class="game-card">Game 1</div>
</div> -->
<style>
	.hero {
		--primary-color: #0c304b;
		--secondary-color: #ffffff;
		--accent-color: #ff8e76;
	}

	.hero {
		font-family: 'Roboto', sans-serif;
		display: flex;
		gap: 6vh;
		align-items: center;
		justify-content: center;
		height: 100vh;
		background-color: var(--primary-color);
		background-image: url('https://www.transparenttextures.com/patterns/stardust.png');
		background-blend-mode: screen;
		color: var(--secondary-color);
		flex-direction: column;
		animation: movingBackground 10s linear infinite;
	}

	@keyframes movingBackground {
		0% {
			background-position: 0 0;
		}
		100% {
			background-position: 100px 50px;
		}
	}

	.hero-title {
		display: flex;
		flex-wrap: wrap;
		gap: 2vw;
		font-size: 5rem;
		font-weight: bold;
		margin: 5vh;
		color: var(--accent-color);
	}

	.title-word {
		animation: color-animation 4s linear infinite;
	}

	.title-word-1 {
		--color-1: #df8453;
		--color-2: #3d8dae;
		--color-3: #e4a9a8;
	}

	.title-word-2 {
		--color-1: #dbad4a;
		--color-2: #accfcb;
		--color-3: #17494d;
	}

	.title-word-3 {
		--color-1: #accfcb;
		--color-2: #e4a9a8;
		--color-3: #accfcb;
	}

	.title-word-4 {
		--color-1: #3d8dae;
		--color-2: #df8453;
		--color-3: #e4a9a8;
	}

	@keyframes color-animation {
		0% {
			color: var(--color-1);
		}
		32% {
			color: var(--color-1);
		}
		33% {
			color: var(--color-2);
		}
		65% {
			color: var(--color-2);
		}
		66% {
			color: var(--color-3);
		}
		99% {
			color: var(--color-3);
		}
		100% {
			color: var(--color-1);
		}
	}

	.hero-description {
		font-size: 1.2rem;
		text-align: center;
		max-width: 800px;
		margin: 0 auto 20px;
		line-height: 1.5;
		background-image: linear-gradient(90deg, #df8453, #3d8dae, #e4a9a8, #accfcb, #17494d);
		background-clip: text;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		letter-spacing: 0.15em;
	}

	.play-btn {
		padding: 12px 24px;
		background-image: linear-gradient(135deg, #3d8dae 0%, #accfcb 100%);
		color: var(--primary-color);
		border: none;
		border-radius: 4px;
		font-size: 1.2rem;
		cursor: pointer;
		transition: all 0.3s ease;
		position: relative;
		overflow: hidden;
	}

	.play-btn::before {
		content: '';
		position: absolute;
		top: -50%;
		left: -50%;
		width: 200%;
		height: 200%;
		background-image: radial-gradient(circle, #accfcb 0%, #3d8dae 100%);
		transform: translateY(-75%) translateX(-75%);
		transition: all 0.3s ease;
		opacity: 0;
		pointer-events: none;
	}

	.play-btn:hover {
		background-image: linear-gradient(135deg, #accfcb 0%, #3d8dae 100%);
		color: var(--secondary-color);
	}

	.play-btn:hover::before {
		transform: translateY(0) translateX(0);
		opacity: 0.25;
	}
</style>
