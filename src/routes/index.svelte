<script>
  import { goto } from '$app/navigation';
  
  function startGame() {
    goto('/game');
  }
</script>

<main class="p-4">
  <h1 class="text-4xl font-bold mb-4">Welcome to Rock Paper Scissors!</h1>
  <p class="mb-2">Rock Paper Scissors is a classic hand game played by two or more people. It is often used as a way of making decisions or resolving disputes. The game is simple: each player simultaneously forms one of three shapes with an outstretched hand. The shapes are "rock" (a fist), "paper" (an open hand), and "scissors" (a fist with the index and middle fingers extended).</p>
  <p class="mb-4">Click the button below to start playing!</p>
  
  <button class="py-2 px-4 bg-blue-500 text-white rounded-md" on:click={startGame}>Start Game</button>
</main>
