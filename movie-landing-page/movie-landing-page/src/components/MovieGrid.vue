<template>
  <section id="movies" class="movie-grid-section">
    <h2 class="section-title">Movie Grid</h2>

    <!-- Search Bar with Search Icon -->
    <div class="search-bar">
      <input
        v-model="searchQuery"
        @keyup.enter="addMovie"
        type="text"
        placeholder="Search movie and press Enter"
      />
      <button class="add-btn" @click="addMovie">
        <img src="/assets/Icons/Search Black.svg" alt="Search" />
      </button>
    </div>

    <!-- Movie Cards Grid -->
    <div class="grid">
     <div class="card" v-for="(movie, idx) in movies" :key="movie.id">
  <div class="poster-container">
    <img
      v-if="movie.image && movie.image.medium"
      :src="movie.image.medium"
      :alt="movie.name"
      class="poster"
    />
    <div v-else class="placeholder">No Image</div>

  
    <button class="close-btn" @click="removeMovie(idx)">
      <img src="/assets/Icons/Close White.svg" alt="Remove" />
    </button>
  </div>

  <h3>{{ movie.name }}</h3>
  <p v-html="shortSummary(movie.summary)"></p>
</div>

    </div>
  </section>
</template>

<script>
export default {
  name: 'MovieGrid',
  data() {
    return {
      movies: [],
      searchQuery: ''
    }
  },
  methods: {
    removeMovie(index) {
      this.movies.splice(index, 1)
    },
    shortSummary(html) {
      const txt = html.replace(/<[^>]+>/g, '')
      return txt.length > 100 ? txt.slice(0, 100) + '…' : txt
    },
    async addMovie() {
      const q = this.searchQuery.trim()
      if (!q) return
      try {
        const res = await fetch(
          `https://api.tvmaze.com/search/shows?q=${encodeURIComponent(q)}`
        )
        const data = await res.json()
        if (data.length > 0) {
          this.movies.push(data[0].show)
          this.searchQuery = ''
        } else {
          alert('No movies found')
        }
      } catch (err) {
        console.error(err)
      }
    }
  },
  async mounted() {
    const ids = [1, 2, 3]
    const promises = ids.map(id =>
      fetch(`https://api.tvmaze.com/shows/${id}`).then(r => r.json())
    )
    this.movies = await Promise.all(promises)
  }
}
</script>

<style scoped>
.movie-grid-section {
  padding: 60px 20px;
  background: #fff;
}
.section-title {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 20px;
  color: #333;
}

/* Search Bar */
.search-bar {
  display: flex;
  justify-content: center;
  margin-bottom: 30px;
}
.search-bar input {
  padding: 8px;
  font-size: 1rem;
  width: 250px;
  border: 1px solid #ccc;
  border-right: none;
  border-radius: 4px 0 0 4px;
}
.search-bar .add-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 8px;
  border: 1px solid #ccc;
  background: #333;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
}
.search-bar .add-btn img {
  width: 20px;
  height: 20px;
}

/* Grid & Cards */
.grid {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
}
.card {
  position: relative;
  background: #f9f9f9;
  border-radius: 8px;
  overflow: hidden;
  padding: 15px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
}
.close-btn {
  position: absolute;
  top: 8px;
  right: 8px;
  background: transparent;
  border: none;
  cursor: pointer;
}
.close-btn img {
  width: 24px;
  height: 24px;
}

/* Movie Image & Placeholder */
.card img {
  width: 100%;
  height: 320px;
  object-fit: cover;
  border-radius: 4px;
}
.card .placeholder {
  width: 100%;
  height: 320px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #ddd;
  color: #666;
  font-size: 1rem;
  border-radius: 4px;
}

.card h3 {
  margin: 12px 0 8px;
  font-size: 1.1rem;
  color: #222;
}
.card p {
  font-size: 0.95rem;
  color: #555;
  line-height: 1.4;
}

/* Only target .poster images */
.card .poster {
  width: 100%;
  height: 320px;
  object-fit: cover;
  border-radius: 4px;
}

/* And style close-btn icon separately */
.card .close-btn img {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

/* Poster container එක position:relative කරලා button එක ඒකේ corner එකට pin වෙන විදිහ */
.poster-container {
  position: relative;
  width: 100%;
  height: 320px;
  overflow: hidden;
  border-radius: 4px;
}

/* Poster image */
.poster-container .poster {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Close button */
.poster-container .close-btn {
  position: absolute;
  top: 8px;      /* ऊपरින් 8px */
  right: 8px;    /* වමෙන් 8px */
  background: rgba(0,0,0,0.6);
  border: none;
  border-radius: 50%;
  padding: 4px;
  cursor: pointer;
  z-index: 2;
}

.poster-container .close-btn img {
  width: 16px;
  height: 16px;
  display: block;
}

/* විශේෂයෙන් placeholder ට height එක ගන්න */
.poster-container .placeholder {
  width: 100%;
  height: 100%;
  background: #ddd;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
}

</style>
