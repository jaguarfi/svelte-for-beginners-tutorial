<script>
  export let poll;

  $: totalVotes = poll.votesA + poll.votesB;
</script>

<div class="poll">
  <h3 class="poll-question">{poll.question}</h3>
  <p>Total votes: {totalVotes}</p>
  <div class="answers">
    <div class="answer">
      <div class="percent percent-a" />
      <span>{poll.answerA} ({poll.votesA})</span>
    </div>
    <div class="answer">
      <div class="percent percent-b" />
      <span>{poll.answerB} ({poll.votesB})</span>
    </div>
  </div>
</div>

<style>
  h3 {
    margin: 0 auto;
    color: #333;
  }
  p {
    margin-top: 6px;
    font-size: 14px;
    color: #666;
    margin-bottom: 30px;
  }
  .answer {
    background-color: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }
  .answer:hover {
    opacity: 0.6;
  }
  span {
    display: inline-block;
    padding: 10px 20px;
  }
</style>
