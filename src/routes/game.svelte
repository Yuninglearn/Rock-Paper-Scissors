<script>
  import { onMount } from 'svelte';
  import { writable } from 'svelte/store';
  import { goto } from '$app/navigation';
  
  let playerChoice;
  let computerChoice;
  let result;
  let score = writable(0);
  
  const choices = ['rock', 'paper', 'scissors'];
  
  function getRandomChoice() {
    const randomIndex = Math.floor(Math.random() * choices.length);
    return choices[randomIndex];
  }
  
  function play(choice) {
    playerChoice = choice;
    computerChoice = getRandomChoice();
    
    if (playerChoice === computerChoice) {
      result = "It's a tie!";
    } else if (
      (playerChoice === 'rock' && computerChoice === 'scissors') ||
      (playerChoice === 'paper' && computerChoice === 'rock') ||
      (playerChoice === 'scissors' && computerChoice === 'paper')
    ) {
      result = 'You win!';
      score.update(n => n + 1);
    } else {
      result = 'Computer wins!';
      score.update(n => n - 1);
    }
  }
  
  onMount(() => {
    if (!playerChoice) {
      goto('/');
    }
  });
</script>

<main class="p-4">
  <h1 class="text-4xl font-bold mb-4">Rock Paper Scissors</h1>
  
  <div class="flex gap-2 mb-4">
    <button class="py-2 px-4 bg-blue-500 text-white rounded-md" on:click={() => play('rock')}>Rock</button>
    <button class="py-2 px-4 bg-blue-500 text-white rounded-md" on:click={() => play('paper')}>Paper</button>
    <button class="py-2 px-4 bg-blue-500 text-white rounded-md" on:click={() => play('scissors')}>Scissors</button>
  </div>
  
  {#if playerChoice}
    <div class="result">
      <p>You chose: {playerChoice}</p>
      <p>Computer chose: {computerChoice}</p>
      <p>{result}</p>
    </div>
  {/if}
  
  <div class="score">
    <p>Score: {$score}</p>
  </div>
</main>
