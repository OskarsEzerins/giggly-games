<script lang="ts">
	import { tripleWordFlicksterData } from './data';

	let words: string[] = [];
	let answer: string = '';
	let userAnswer: string[] = [];
	let isCorrect: boolean | null = null;

	const getRandomChallenge = (): [string, string[]] => {
		const movieTitles = Object.keys(tripleWordFlicksterData);
		const randomIndex = Math.floor(Math.random() * movieTitles.length);
		const randomMovie = movieTitles[randomIndex];
		const randomWords = tripleWordFlicksterData[randomMovie];
		return [randomMovie, randomWords];
	};

	const generateNewChallenge = () => {
		[answer, words] = getRandomChallenge();
		userAnswer = Array(answer.length).fill('');
		isCorrect = null;
	};

	const checkAnswer = () => {
		isCorrect = userAnswer.join('').toLowerCase() === answer.toLowerCase();

		setTimeout(() => {
			if (isCorrect) {
				generateNewChallenge();
			}

			isCorrect = null;
		}, 1000);
	};

	const updateLetter = (index: number, letter: string) => (userAnswer[index] = letter);

	const handleInput = (event: KeyboardEvent, index: number) => {
		const target = event.target as HTMLInputElement;
		const cursorPosition = target.selectionStart;

		if (
			event.key === 'ArrowRight' &&
			cursorPosition === target.value.length &&
			index < userAnswer.length - 1
		) {
			document.getElementById(`input-${index + 1}`)?.focus();
		} else if (event.key === 'ArrowLeft' && cursorPosition === 0 && index > 0) {
			document.getElementById(`input-${index - 1}`)?.focus();
		} else if (/[A-Za-z]/.test(event.key) && event.key.length === 1) {
			updateLetter(index, event.key);
			if (index < userAnswer.length - 1) {
				setTimeout(() => {
					document.getElementById(`input-${index + 1}`)?.focus();
				}, 0);
			}
		}
	};

	// Generate the initial challenge
	generateNewChallenge();
</script>

<div class="container">
	<h1>Triple Word Flickster</h1>
	<p>Guess the movie from three neon-lit words!</p>
	<div>
		{#each words as word (word)}
			<span class="word">{word}</span>
		{/each}
	</div>
	<div class="input-container">
		{#each userAnswer as letter, index (index)}
			<input
				type="text"
				id="input-{index}"
				bind:value={userAnswer[index]}
				maxlength="1"
				on:keyup={(event) => handleInput(event, index)}
			/>
		{/each}
	</div>
	<button on:click={checkAnswer}>Check</button>
	<br />
	<button on:click={generateNewChallenge}>Skip</button>
	{#if isCorrect !== null}
		<div class="notification {isCorrect ? 'correct' : 'wrong'}">
			{isCorrect ? 'Correct! Well done!' : 'Incorrect. Try again!'}
		</div>
	{/if}
</div>

<style>
	:root {
		--background-color: #222;
		--primary-color: #0ff;
		--secondary-color: #ff0;
		--success-color: #0f0;
		--error-color: #f00;
		--text-color: #fff;
		--text-alternative-color: #222;
	}

	.container {
		min-height: 90vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20px;
		background-color: var(--background-color);
		color: var(--text-color);
		font-family: 'Courier New', monospace;
	}

	h1 {
		font-size: 2rem;
		text-transform: uppercase;
		color: var(--primary-color);
		margin-bottom: 10px;
	}

	p {
		font-size: 1.2rem;
		text-align: center;
		margin-bottom: 20px;
	}

	.word {
		display: inline-block;
		margin: 0 5px;
		font-weight: bold;
		font-size: 1.3rem;
		text-transform: uppercase;
		color: var(--secondary-color);
		text-shadow: 0 0 5px var(--secondary-color);
	}

	.input-container {
		display: flex;
		flex-wrap: wrap;
		margin: 20px 0;
	}

	input {
		width: 20px;
		height: 20px;
		text-align: center;
		margin: 0 2px;
		font-size: 1.2rem;
		background-color: transparent;
		border: 2px solid var(--primary-color);
		color: var(--text-color);
		outline: none;
		transition: border-color 0.3s;
	}

	input:focus {
		border-color: var(--secondary-color);
	}

	button {
		cursor: pointer;
		background-color: var(--primary-color);
		border: none;
		padding: 5px 10px;
		font-size: 1.2rem;
		color: var(--text-alternative-color);
		text-transform: uppercase;
		margin-left: 5px;
		outline: none;
		transition: background-color 0.3s;
	}

	button:hover {
		background-color: var(--secondary-color);
	}

	button:focus {
		border: var(--secondary-color) 2px solid;
	}

	.notification {
		font-size: 1.2rem;
		margin-top: 10px;
	}

	.notification.correct {
		color: var(--success-color);
	}

	.notification.wrong {
		color: var(--error-color);
	}
</style>
