<script>
  import Modal from './components/Modal.svelte';
  import AddPersonForm from "./components/AddPersonForm.svelte";
  export let firstName = 'John';
  export let lastName = 'Doe';

  let beltColour = 'black';
  let showModal = false;

  $: name = `${firstName} ${lastName}`;
  $: {
    console.log(name);
    console.log(beltColour);
  }

  let students = [
    {name: 'Juan Paez', beltColour: 'black', age: 25, skills:['running, fighting'], id: 1},
    {name: 'Camilo Sanchez', beltColour: 'orange', age: 28, skills:['fighting'], id: 2},
    {name: 'Luigi Bros', beltColour: 'brown', age: 35, skills:[], id: 3}
  ];

  const handleDelete = (id) => {
    students = students.filter((student) => student.id !== id);
  };

  const toggleModal = () => {
	showModal = !showModal;
  };

  const handleAddStudent = (e) => {
	const student = e.detail;
	students = [...students, student];
	toggleModal();
  };
</script>

<Modal msg='Sign up for offers' isPromo={true} {showModal} on:click={toggleModal}>

<h3 slot="title">Add a new person</h3>
<AddPersonForm on:addPerson={handleAddStudent}/>
</Modal>
<main>
  <h1>Hello {name}!</h1>
  <button on:click={toggleModal}>Open Modal</button>
  <p style="color: {beltColour}">You are a Ninja with {beltColour} belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="text" bind:value={beltColour} />
  {#each students as student (student.id)}
    <div>
      <h2>{student.name}</h2>
      <p style="color: {student.beltColour}">You are a Ninja with {student.beltColour} belt</p>
      <p>{student.age} years old.</p>
	  <p>{student.skills.length > 0 ? `You have the following skills: ${student.skills.join(', ')}`: `Please add your skills.`}</p>
      <button on:click={() => handleDelete(student.id)}>Delete</button>
    </div>
  {:else}
    <p>There are no students</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
