<template>
  <div>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-md navbar-dark" :style="{ backgroundColor: 'var(--brand-900)' }">
      <div class="container">
        <a class="navbar-brand fw-semibold" href="#">Alex Lopez</a>

        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#nav"
                aria-controls="nav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>

        <div id="nav" class="collapse navbar-collapse">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item"><router-link class="nav-link" to="/">Home</router-link></li>
            <!-- future pages:
            <li class="nav-item"><router-link class="nav-link" to="/projects">Projects</router-link></li>
            <li class="nav-item"><router-link class="nav-link" to="/about">About</router-link></li>
            <li class="nav-item"><router-link class="nav-link" to="/contact">Contact</router-link></li>
            -->
          </ul>
        </div>
      </div>
    </nav>

    <router-view />
  </div>
</template>

<script setup>
// no logic needed yet
</script>

<style>
/* ---- color palette ---- */
:root{
  --brand-900: #0f172a; /* midnight */
  --brand-700: #1e293b;
  --accent-500: #06b6d4; /* cyan accent */
  --text-900:  #0b1220;
  --text-600:  #475569;
  --bg-50:     #f8fafc;
  --card-100:  #eef2f6;
}
body{ background: var(--bg-50); color: var(--text-900); }
a{ text-decoration:none; }
</style>