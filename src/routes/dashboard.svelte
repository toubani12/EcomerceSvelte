<script>
    import { onMount } from 'svelte';
  
    let isAuthenticated = false;
  
    onMount(() => {
      const token = localStorage.getItem('token');
      if (token) {
        isAuthenticated = true;
      } else {
        window.location.href = '/login'; // Redirect to login if not authenticated
      }
    });
  </script>
  
  {#if isAuthenticated}
    <h2>Welcome to the Dashboard</h2>
    <!-- Add your dashboard content here -->
  {/if}
  