<script>
  import ContactCard from './ContactCard.svelte';

  let name = 'Lee';
  let title = '';
  let image = '';
  let description = '';
  let age = 28;

  $: uppercaseName = name.toUpperCase();
  $: console.log(name);
  $: if (name === 'Sun-Kee') {
    age = 26;
  }

  function ageIncrement() {
    age += 1;
  }

  function changeName() {
    name = 'Sun-Kee';
  }

  function nameInput(event) {
    const enteredValue = event.target.value;
    name = enteredValue;
  }
</script>

<h1>My name is {uppercaseName}! I'm {age}years old.</h1>
<button on:click={ageIncrement}>Change Age</button>
<!-- <button on:click={changeName}>Change name</button> -->
<!-- <input type="text" value="{name}" on:input={nameInput}> -->
<input type="text" bind:value={name} />
<input type="text" bind:value={title} />
<input type="text" bind:value={image} />
<textarea rows="3" bind:value={description} />
<ContactCard userName={name} jobTitle={title} {description} userImage={image} />

<style>
  h1 {
    color: purple;
  }
</style>
