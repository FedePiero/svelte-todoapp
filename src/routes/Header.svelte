<script>
  import { page } from "$app/stores";
</script>

<header>
  <nav class="bg-gray-900 shadow-md">
    <ul>
      <li aria-current={$page.url.pathname === "/" ? "page" : undefined}>
        <a href="/">Home</a>
      </li>
      <li aria-current={$page.url.pathname === "/about" ? "page" : undefined}>
        <a href="/about">About</a>
      </li>
    </ul>
  </nav>
</header>

<style>
  header {
    width: 100%;
  }
  ul {
    position: relative;
    padding: 0;
    margin: 0;
    height: 3em;
    display: flex;
    justify-content: center;
    align-items: center;
    list-style: none;
    background-size: contain;
  }
  li {
    position: relative;
    height: 100%;
  }
  nav a {
    display: flex;
    height: 100%;
    align-items: center;
    padding: 0 0.5rem;
    font-weight: 800;
    font-size: 1rem;
    color: white;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    text-decoration: none;
    transition: color 0.2s linear;
  }
</style>
