<template>
  <section class="hero">
    <p class="eyebrow"><span class="dot"></span> TEST ENVIRONMENT / 001</p>
    <h1>A little movement.<br /><span>A bigger picture.</span></h1>
    <p class="intro">
      The test bench for Bodymo Tracker. A small place to check the basics while
      we build the full experience.
    </p>
    <RouterLink class="button" to="/setup"
      >Open setup <span aria-hidden="true">↗</span></RouterLink
    >
  </section>
  <section class="cards" aria-label="Project components">
    <article v-for="(item, index) in components" :key="item.name" class="card">
      <div class="card-top">
        <span>0{{ index + 1 }}</span
        ><span class="tag">PLANNED</span>
      </div>
      <h2>{{ item.name }}</h2>
      <p>{{ item.description }}</p>
    </article>
  </section>
  <p class="note">
    Just the essentials for now. Device connection, configuration, and live
    tracking will come later.
  </p>
</template>

<script setup>
const components = [
  { name: "Sol", description: "A reserved space for the Sol component." },
  { name: "Terra", description: "The tracker’s MCU and dual-IMU firmware." },
  { name: "Luna", description: "The companion sensor, handled by Terra." },
];
</script>
