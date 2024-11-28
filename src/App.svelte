<script>
	import { Router, Route, Link } from 'svelte-routing';
	import Login from './routes/login.svelte';
	import CreateUser from './routes/create-user.svelte';
	import Dashboard from './routes/dashboard.svelte'; // Add your dashboard page later
  </script>
  
  <Router>
	<nav>
	  <Link to="/">Home</Link>
	  <Link to="/login">Login</Link>
	  <Link to="/create-user">Create User</Link>
	</nav>
  
	<Route path="/login" component={Login} />
	<Route path="/create-user" component={CreateUser} />
	<Route path="/dashboard" component={Dashboard} />
  </Router>
  