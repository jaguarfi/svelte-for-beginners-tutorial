<script>
  import PollStore from '../stores/PollStore';
  import Card from '../shared/Card.svelte';
  import Button from '../shared/Button.svelte';
  export let poll;

  $: totalVotes = poll.votesA + poll.votesB;
  $: percentA = totalVotes ? (poll.votesA / totalVotes) * 100 : 0;
  $: percentB = totalVotes ? (poll.votesB / totalVotes) * 100 : 0;

  const handleVote = (option, id) => {
    PollStore.update((polls) => {
      return polls.map((poll) => {
        if (poll.id === id) {
          if (option === 'a') {
            poll.votesA++;
          } else {
            poll.votesB++;
          }
        }
        return poll;
      });
    });
  };
</script>

<Card>
  <div class="poll">
    <h3 class="poll-question">{poll.question}</h3>
    <p>Total votes: {totalVotes}</p>
    <div class="answers">
      <div class="answer" on:click={() => handleVote('a', poll.id)}>
        <div class="percent percent-a" style="width: {percentA}%" />
        <span>{poll.answerA} ({poll.votesA})</span>
      </div>
      <div class="answer" on:click={() => handleVote('b', poll.id)}>
        <div class="percent percent-b" style="width: {percentB}%" />
        <span>{poll.answerB} ({poll.votesB})</span>
      </div>
    </div>
    <div class="delete">
      <Button flat={true} on:click={() => PollStore.update((polls) => polls.filter((p) => p.id !== poll.id))}>
        Delete</Button>
    </div>
  </div>
</Card>

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
  .percent {
    height: 100%;
    box-sizing: border-box;
    position: absolute;
    top: 0;
    left: 0;
    transition: width 0.5s ease;
  }

  .percent-a {
    border-left: 4px solid #2395d2;
    background-color: hsla(201, 71%, 48%, 0.2);
  }

  .percent-b {
    border-left: 4px solid #ab4212;
    background-color: rgb(171, 166, 28, 0.2);
  }

  .delete {
    text-align: center;
    margin-top: 30px;
  }
</style>
