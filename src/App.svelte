<script>
  import Footer from './components/Footer.svelte';
  import Header from './components/Header.svelte';
  import Tabs from './shared/Tabs.svelte';
  import PollList from './components/PollList.svelte';
  import AddPollForm from './components/AddPollForm.svelte';

  let tabs = ['Current Polls', 'Add Poll'];
  let polls = [];
  let activeItem = tabs[0];

  const handleChangeTab = (e) => {
    activeItem = e.detail;
  };

  const handleAddPoll = (e) => {
    polls = [e.detail, ...polls];
    activeItem = tabs[0];
    console.log(e.detail);
  };

  const handleVote = (e) => {
    polls = polls.map((poll) => {
      if (poll.id === e.detail.id) {
        if (e.detail.option === 'a') {
          poll.votesA++;
        } else {
          poll.votesB++;
        }
      }
      return poll;
    });
  };
</script>

<Header />
<main>
  <h1>Start here!</h1>
  <Tabs on:changeTab={handleChangeTab} {tabs} {activeItem} />
  {#if tabs[0] === activeItem}
        <PollList {polls} on:vote={handleVote}/>
  {:else if tabs[1] === activeItem}
    <AddPollForm on:addPoll={handleAddPoll}/>
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
