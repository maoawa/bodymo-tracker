<template>
  <div class="shell">
    <header>
      <RouterLink class="brand" to="/" aria-label="Bodymo home"
        ><span class="brand-mark">b.</span> bodymo<span class="brand-sub"
          >/ tracker</span
        ></RouterLink
      >
      <nav aria-label="Main navigation">
        <RouterLink to="/">Overview</RouterLink
        ><RouterLink to="/setup">Setup</RouterLink>
      </nav>
    </header>
    <main><RouterView /></main>
    <footer>
      <span>BODYMO / DEVELOPMENT LAB</span
      ><span>Temporary test site · No hardware connected</span>
    </footer>
  </div>
</template>
