<script>
    let username = '';
    let password = '';
    let name = '';
    let email = '';
    let errorMessage = '';
  
    const createUser = async () => {
      try {
        const response = await fetch('http://localhost:8080/api/users', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({
            username,
            password,
            name,
            email,
          }),
        });
  
        if (!response.ok) {
          throw new Error('Failed to create user');
        }
  
        const data = await response.json();
        alert('User created successfully');
        // Redirect or clear form if necessary
      } catch (error) {
        errorMessage = error.message;
      }
    };
  </script>
  
  <h2>Create User</h2>
  <form on:submit|preventDefault={createUser}>
    <div>
      <label for="username">Username</label>
      <input type="text" id="username" bind:value={username} required />
    </div>
    <div>
      <label for="password">Password</label>
      <input type="password" id="password" bind:value={password} required />
    </div>
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" bind:value={name} required />
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" id="email" bind:value={email} required />
    </div>
    <div>
      <button type="submit">Create User</button>
    </div>
  </form>
  
  {#if errorMessage}
    <p>{errorMessage}</p>
  {/if}
  