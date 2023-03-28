<script>
  import Footer from './components/Footer.svelte';
  import Header from './components/Header.svelte';
  import Tabs from './shared/Tabs.svelte';
  import AddPollForm from './components/AddPollForm.svelte';

  let tabs = ['Current Polls', 'Add Poll'];
  let activeItem = tabs[0];

  const handleChangeTab = (e) => {
    activeItem = e.detail;
  };
</script>

<Header />
<main>
  <h1>Start here!</h1>
  <Tabs on:changeTab={handleChangeTab} {tabs} {activeItem} />
  {#if tabs[0] === activeItem}
    <!-- <CurrentPolls /> -->
    <p>Current Polls</p>
  {:else if tabs[1] === activeItem}
    <AddPollForm />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
