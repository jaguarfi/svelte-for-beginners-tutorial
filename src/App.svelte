<script>
  import Footer from './components/Footer.svelte';
  import Header from './components/Header.svelte';
  import Tabs from './shared/Tabs.svelte';
  import PollList from './components/PollList.svelte';
  import AddPollForm from './components/AddPollForm.svelte';
  import PollStore from './stores/PollStore';

  let tabs = ['Current Polls', 'Add Poll'];
  let polls = [];
  PollStore.subscribe((data) => {
    polls = data;
  });
  let activeItem = tabs[0];

  const handleChangeTab = (e) => {
    activeItem = e.detail;
  };

  const handleAddPoll = (e) => {
    activeItem = tabs[0];
  };
</script>

<Header />
<main>
  <h1>Start here!</h1>
  <Tabs on:changeTab={handleChangeTab} {tabs} {activeItem} />
  {#if tabs[0] === activeItem}
    <PollList />
  {:else if tabs[1] === activeItem}
    <AddPollForm on:addPoll={handleAddPoll} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
