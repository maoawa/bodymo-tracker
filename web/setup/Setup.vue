<script setup>
import { ref } from "vue";
const count = ref(0);
const checked = ref(false);
</script>

<template>
  <section class="hero setup-hero">
    <p class="eyebrow"><span class="dot"></span> SETUP / SMOKE TEST</p>
    <h1>Start with<br /><span>the basics.</span></h1>
    <p class="intro">
      This is a temporary browser-only check. It does not connect to a tracker,
      flash firmware, or save device settings.
    </p>
  </section>
  <section class="test-panel" aria-labelledby="test-title">
    <div>
      <p class="eyebrow">01 / INTERACTION</p>
      <h2 id="test-title">Is everything responding?</h2>
      <p>Use the controls below to check that Vue is running.</p>
    </div>
    <label class="check"
      ><input v-model="checked" type="checkbox" /> I can interact with this
      page</label
    >
    <div class="test-actions">
      <button class="button" @click="count++">
        Run test <span aria-hidden="true">↗</span></button
      ><button
        class="secondary"
        @click="
          count = 0;
          checked = false;
        "
      >
        Reset
      </button>
    </div>
    <p class="result" role="status" aria-live="polite">
      {{
        count
          ? `Interaction passed · ${count} test${count === 1 ? "" : "s"} run`
          : "Ready when you are."
      }}{{ checked ? " · Checkbox confirmed" : "" }}
    </p>
  </section>
  <p class="note">
    Nothing is stored or sent. Refreshing the page resets this test.
  </p>
</template>
