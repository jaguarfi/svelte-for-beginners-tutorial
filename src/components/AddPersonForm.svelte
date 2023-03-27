<script>
  let name;
  let beltColour;
  let age;
  let skills = [];
  const handleSubmit = (e) => {
    console.log(name, beltColour, age, skills);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <label>Belt Colour</label>
  <select bind:value={beltColour}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>
  <input type="number" placeholder="age" name="age" bind:value={age} />
  <label>Skills:</label>
  <input type="checkbox" name="fighting" value="fighting" bind:group={skills} />fighting<br />
  <input type="checkbox" name="sneaking" value="sneaking" bind:group={skills} />sneaking<br />
  <input type="checkbox" name="running" value="running" bind:group={skills} />running<br />
  <button>Add Person</button>
</form>

<style></style>
