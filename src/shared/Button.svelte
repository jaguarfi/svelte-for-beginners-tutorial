<script>
  export let type = 'primary';
  export let flat = false;
  export let inverse = false;
</script>

<button class={type} class:flat class:inverse on:click>
  <slot />
</button>

<style>
  button {
    border: none;
    border-radius: 6px;
    padding: 10px 16px;
    font-size: 18px;
    cursor: pointer;
    box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
  }

  .primary {
    background-color: #d91b42;
    color: #fff;
  }
  .primary:hover,
  .primary:focus {
    background-color: #b71a3a;
  }

  .primary:active {
    background-color: #a71a3a;
    box-shadow: none;
  }

  .secondary {
    background-color: #1b74d9;
    color: #fff;
  }

  .secondary:hover,
  .secondary:focus {
    background-color: #1a5eb7;
  }

  .secondary:active {
    background-color: #0f3e7c;
    box-shadow: none;
  }

  .flat {
    box-shadow: none;
  }

  .inverse.primary {
    background-color: #fff;
    color: #d91b42;
  }

  .inverse.primary:hover,
  .inverse.primary:focus {
    background-color: #f2f2f2;
  }

  .inverse.primary:active {
    background-color: #e6e6e6;
    box-shadow: none;
  }

  .inverse.secondary {
    background-color: #fff;
    color: #1b74d9;
  }

  .inverse.secondary:hover,
  .inverse.secondary:focus {
    background-color: #f2f2f2;
  }

  .inverse.secondary:active {
    background-color: #e6e6e6;
    box-shadow: none;
  }
</style>
