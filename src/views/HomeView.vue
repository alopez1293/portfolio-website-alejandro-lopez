<template>
  <main class="py-5">
    <div class="container">
      <!-- hero -->
      <div class="row align-items-center g-4">
        <div class="col-12 col-lg-7">
          <span class="badge mb-3" :style="{ backgroundColor: 'var(--accent-500)' }">
            Aspiring Full-Stack Developer
          </span>
          <h1 class="display-5 fw-bold mb-3">Hi, I’m Alex Lopez.</h1>
          <p class="lead" style="color: var(--text-600)">
            I’m building a professional foundation in web development with a focus on
             responsive UI, and clean, maintainable code.
            This semester I’ll expand this site with interactive projects and course highlights.
              
          </p>

          <div class="d-flex flex-wrap gap-3 mt-4">
            <a class="btn btn-dark btn-lg" :style="{ backgroundColor: 'var(--brand-900)' }" href="https://github.com" target="_blank" rel="noopener">GitHub</a>
            <a class="btn btn-outline-dark btn-lg" href="https://www.linkedin.com/in/alejandro-lopez-jauregui-4b4056201" target="_blank" rel="noopener">LinkedIn</a>
            <a class="btn btn-outline-dark btn-lg" href="alopez1293@gmail.com">Email Me</a>
          </div>
        </div>

        <div class="col-12 col-lg-5 d-flex justify-content-lg-end">
          <figure class="card shadow-sm border-0" style="max-width: 360px; background: var(--card-100)">
            <img class="card-img-top" src="@/assets/profile.jpg" alt="Professional portrait of Alex Lopez" />
            <figcaption class="card-body">
              <p class="mb-0" style="color: var(--text-600)">Based in Nebraska • Open to internships</p>
            </figcaption>
          </figure>
        </div>
      </div>

      <!-- quick facts using CSS Grid -->
      <section class="mt-5">
        <div class="grid-cards">
          <div class="p-4 rounded" style="background:white">
            <h2 class="h5 fw-semibold mb-2">Skills</h2>
            <ul class="mb-0">
              <li>Vue 3</li>
              <li>HTML, CSS, Bootstrap</li>
              <li>Git & GitHub</li>
            </ul>
          </div>
          <div class="p-4 rounded" style="background:white">
            <h2 class="h5 fw-semibold mb-2">Focus Areas</h2>
            <ul class="mb-0">
              <li>Responsive UI</li>
              <li>Clean, commented code</li>
            </ul>
          </div>
          <div class="p-4 rounded" style="background:white">
            <h2 class="h5 fw-semibold mb-2">This Semester</h2>
            <p class="mb-2" style="color: var(--text-600)">
              I’ll add Projects, About, and Contact pages using Vue Router and enhance the site with dynamic components.
            </p>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<script setup>
// static content for now
</script>

<style scoped>
.grid-cards{
  display:grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap:1rem;
}
</style>