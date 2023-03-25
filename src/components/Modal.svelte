<script>
  export let showModal = false;
</script>

{#if showModal}
  <div class="backdrop">
    <div class="modal">
      <p>Sign up for more!</p>
    </div>
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
</style>
