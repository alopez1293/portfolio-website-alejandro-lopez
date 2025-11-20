<template>
  <main class="py-5">
    <div class="container">
      <h1 class="mb-3">Portfolio</h1>
      <p class="text-muted mb-4">
        These projects are pulled live from my GitHub account to showcase what I’ve been working on.
      </p>

      <!-- Loading state -->
      <div v-if="isLoading" class="alert alert-info">
        Loading repositories...
      </div>

      <!-- Error state -->
      <div v-else-if="errorMessage" class="alert alert-danger">
        {{ errorMessage }}
      </div>

      <!-- No repos state -->
      <div v-else-if="repos.length === 0" class="alert alert-secondary">
        No repositories found. Make sure you have public repos on GitHub.
      </div>

      <!-- Repos list -->
      <section v-else class="repos-grid">
        <article
          v-for="repo in repos"
          :key="repo.id"
          class="card shadow-sm border-0 h-100"
        >
          <div class="card-body d-flex flex-column">
            <!-- Repo name -->
            <h2 class="h5 card-title">
              <a
                :href="repo.html_url"
                target="_blank"
                rel="noopener"
                class="stretched-link"
              >
                {{ repo.name }}
              </a>
            </h2>

            <!-- Description -->
            <p class="card-text text-muted mb-3">
              {{ repo.description || 'Description coming soon.' }}
            </p>

            <!-- Meta info -->
            <div class="mt-auto small text-muted">
              <div>
                <strong>Language:</strong>
                {{ repo.language || 'N/A' }}
              </div>
              <div>
                <strong>Last updated:</strong>
                {{ formatDate(repo.updated_at) }}
              </div>
            </div>
          </div>
        </article>
      </section>
    </div>
  </main>
</template>

<script setup>
// Composition API: simple and powerful for this

import { ref, onMounted } from 'vue'

// 1. GitHub username
const GITHUB_USERNAME = 'alopez1293'

// 2. Reactive state
const repos = ref([])
const isLoading = ref(true)
const errorMessage = ref('')

// 3. Helper to format GitHub's ISO dates nicely
const formatDate = (isoString) => {
  if (!isoString) return 'Unknown'
  return new Date(isoString).toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'short',
    day: 'numeric'
  })
}

// 4. Function to fetch repos from GitHub
const fetchRepos = async () => {
  isLoading.value = true
  errorMessage.value = ''

  try {
    const response = await fetch(
      `https://api.github.com/users/${GITHUB_USERNAME}/repos?sort=updated`
    )

    if (!response.ok) {
      // e.g. 404, 500, rate limit, etc.
      throw new Error(`GitHub API returned status ${response.status}`)
    }

    const data = await response.json()
    // data is an array of repo objects
    repos.value = data
  } catch (error) {
    console.error(error)
    errorMessage.value =
      'Sorry, something went wrong loading your GitHub projects. Please try again later.'
  } finally {
    isLoading.value = false
  }
}

// 5. Run fetch when the component first appears
onMounted(() => {
  fetchRepos()
})
</script>

<style scoped>
/* Simple responsive grid for repo cards */
.repos-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1rem;
}
</style>
