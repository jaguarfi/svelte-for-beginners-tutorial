<script>
  export let polls = [];
</script>

<div class="poll-list">
  {#each polls as poll (poll.id)}
    <div class="poll-question">{poll.question}</div>
    <div class="answers">
      <div class="answer">
        <div class="answer-text">{poll.answerA}</div>
      </div>
      <div class="answer">
        <div class="answer-text">{poll.answerB}</div>
      </div>
    </div>
  {:else}
    <p>Please add a new poll</p>
  {/each}
</div>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>
