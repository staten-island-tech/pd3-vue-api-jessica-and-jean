<template>
  <div>
    <nav>
      <RouterLink to="/Data">Data</RouterLink>
      <RouterLink to="/BarChart">Bar Chart</RouterLink>
      <RouterLink to="/PieChart">Pie Chart</RouterLink>
    </nav>
    <RouterView />
  </div>
</template>

<script></script>

<style scoped>
body {
  margin: 0;
}
nav {
  font-family: 'Gill Sans Extrabold', sans-serif;
  letter-spacing: 0.1rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 100%;
  text-align: center;
  padding: 1rem 0rem 1rem 0rem;
}
nav a {
  font-size: 1.2rem;
  color: #9c7ddb;
  display: flex;
  justify-content: center;
  padding: 0 1rem;
  margin: 0.5rem;
  width: fit-content;
  white-space: nowrap;
  text-decoration: none;
}
nav a:first-of-type {
  border: none;
}
nav a.router-link-active {
  opacity: 60%;
}
nav a.router-link-exact-active:hover {
  background-color: transparent;
}
nav a:hover {
  opacity: 60%;
  transition: all 1s ease;
}
</style>