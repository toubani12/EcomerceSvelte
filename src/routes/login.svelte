<script>
    let username = '';
    let password = '';
    let errorMessage = '';
  
    const login = async () => {
      try {
        const response = await fetch('http://localhost:8080/api/auth/login', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            username,
            password
          })
        });
  
        if (!response.ok) {
          throw new Error('Login failed');
        }
  
        const data = await response.json();
        localStorage.setItem('token', data.token); // Store JWT token
        window.location.href = '/dashboard'; // Redirect to a protected page
      } catch (error) {
        errorMessage = error.message;
      }
    };
  </script>
  
  <h2>Login</h2>
  <form on:submit|preventDefault={login}>
    <div>
      <label for="username">Username</label>
      <input type="text" id="username" bind:value={username} required />
    </div>
    <div>
      <label for="password">Password</label>
      <input type="password" id="password" bind:value={password} required />
    </div>
    <div>
      <button type="submit">Login</button>
    </div>
  </form>
  
  {#if errorMessage}
    <p>{errorMessage}</p>
  {/if}
  