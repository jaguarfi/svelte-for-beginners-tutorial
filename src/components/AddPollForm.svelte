<script>
  import {createEventDispatcher} from 'svelte';

  const dispatch = createEventDispatcher();
  let fields = {
    property: '',
    answerA: '',
    answerB: ''
  };

  const handleSubmit = () => {
    dispatch('addPoll', fields);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <div class="form-field">
    <label for="question">Poll Question:</label>
    <input type="text" id="question" bind:value={fields.question} />
  </div>
  <div class="form-field">
    <label for="answer-a">Answer A:</label>
    <input type="text" id="answer-a" bind:value={fields.answerA} />
  </div>
  <div class="form-field">
    <label for="answer-b">Answer B:</label>
    <input type="text" id="answer-b" bind:value={fields.answerB} />
  </div>
  <button>Add Poll</button>
</form>

<style>
  form {
    max-width: 400px;
    margin: 0 auto;
    text-align: center;
  }
  .form-field {
    margin: 18px auto;
  }
  input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 6px;
  }

  label {
    margin: 10px auto;
    text-align: left;
    margin-bottom: 10px;
  }
</style>
