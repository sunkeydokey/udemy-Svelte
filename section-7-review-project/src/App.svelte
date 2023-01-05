<script>
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte';
  import TextInput from './UI/TextInput.svelte';
  import Button from './UI/Button.svelte';

  let title = '';
  let subtitle = '';
  let address = '';
  let email = '';
  let description = '';
  let imageUrl = '';

  let meetups = [
    {
      id: 'm1',
      title: 'Svelte',
      subtitle: 'Learn Svelte',
      description: '13hour Svelte Course',
      imageUrl:
        'https://images.unsplash.com/photo-1593720213428-28a5b9e94613?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80',
      address: '273',
      contactEmail: 'www@dot.com',
    },
    {
      id: 'm2',
      title: 'React',
      subtitle: 'Learn React',
      description: 'How to code React',
      imageUrl:
        'https://images.unsplash.com/photo-1633356122544-f134324a6cee?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80',
      address: '123',
      contactEmail: 'react@facebook.com',
    },
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      address: address,
      email: email,
      description: description,
      imageUrl: imageUrl,
    };

    meetups = [newMeetup, ...meetups];
  }
</script>

<Header />

<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      type="text"
      label="Title"
      value={title}
      on:input={(title) => event.target.value}
    />

    <TextInput
      id="subtitle"
      label="Subtitle"
      type="text"
      value={subtitle}
      on:input={(subtitle) => event.target.value}
    />

    <TextInput
      id="address"
      label="Address"
      type="text"
      value={address}
      on:input={(address) => event.target.value}
    />

    <TextInput
      id="imageUrl"
      label="Image URL"
      type="text"
      value={imageUrl}
      on:input={(imageUrl) => event.target.value}
    />

    <TextInput
      id="email"
      label="E-mail"
      type="email"
      value={email}
      on:input={(email) => event.target.value}
    />

    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      value={description}
      rows="3"
      on:input={(description) => event.target.value}
    />

    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} />
</main>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>
