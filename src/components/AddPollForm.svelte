<script>
  import {createEventDispatcher} from 'svelte';
  import Button from '../shared/Button.svelte';
  import PollStore from '../stores/PollStore';
  import {v4 as uuidv4} from 'uuid';

  const dispatch = createEventDispatcher();
  let fields = {
    question: '',
    answerA: '',
    answerB: ''
  };

  let errors = {
    question: '',
    answerA: '',
    answerB: ''
  };

  let valid = false;

  const handleSubmit = () => {
    valid = true;
    if (fields.question.trim().length < 5) {
      errors.question = 'Question must be at least 5 characters';
      valid = false;
    } else {
      errors.question = '';
    }
    if (fields.answerA.trim().length < 1) {
      errors.answerA = 'Answer A must be at least 2 characters';
      valid = false;
    } else {
      errors.answerA = '';
    }
    if (fields.answerB.trim().length < 1) {
      errors.answerB = 'Answer B must be at least 2 characters';
      valid = false;
    } else {
      errors.answerB = '';
    }

    if (valid) {
      let poll = {...fields, votesA: 0, votesB: 0, id: uuidv4()};
      PollStore.update((polls) => [poll, ...polls]);
      dispatch('addPoll');
    }
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <div class="form-field">
    <label for="question">Poll Question:</label>
    <input type="text" id="question" bind:value={fields.question} />
    <div class="error">{errors.question}</div>
  </div>
  <div class="form-field">
    <label for="answer-a">Answer A:</label>
    <input type="text" id="answer-a" bind:value={fields.answerA} />
    <div class="error">{errors.answerA}</div>
  </div>
  <div class="form-field">
    <label for="answer-b">Answer B:</label>
    <input type="text" id="answer-b" bind:value={fields.answerB} />
    <div class="error">{errors.answerB}</div>
  </div>
  <Button type={'secondary'} flat={false} inverse={false}>Add Poll</Button>
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

  .error {
    font-weight: bold;
    color: #d91b42;
    font-size: 12px;
  }
</style>
