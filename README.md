# Fiesta-filmz
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fiesta Films - Home of Rwandan Cinema</title>
  <style>
    /* ==========================================================================
       Fiesta Films - Global Styles & Design System
       ========================================================================== */
    :root {
      --bg-color: #0b0c10;
      --surface-color: #12141d;
      --surface-card: #1f222e;
      --border-color: #2a2e3d;
      --text-main: #f0f2f5;
      --text-muted: #a0a5b5;
      --primary-red: #e50914;
      --primary-red-hover: #b80710;
      --accent-gold: #ffb703;
      --accent-gold-hover: #dda15e;
      --font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      --transition-fast: 0.2s ease;
      --transition-normal: 0.3s ease;
      --radius-sm: 6px;
      --radius-md: 10px;
      --radius-lg: 16px;
      --box-shadow: 0 8px 24px rgba(0,0,0,0.5);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      background-color: var(--bg-color);
      color: var(--text-main);
      font-family: var(--font-family);
      line-height: 1.5;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    a { color: inherit; text-decoration: none; }
    img { max-width: 100%; display: block; }
    button, input, select, textarea { font-family: inherit; font-size: 1rem; }

    .container {
      width: 100%;
      max-width: 1280px;
      margin: 0 auto;
      padding: 0 1.5rem;
    }
    .main-content { flex: 1; }

    .text-gold { color: var(--accent-gold); }
    .text-red { color: var(--primary-red); }
    .text-muted { color: var(--text-muted); }

    /* Buttons */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      padding: 0.75rem 1.5rem;
      border-radius: var(--radius-md);
      font-weight: 600;
      cursor: pointer;
      border: none;
      transition: all var(--transition-fast);
    }
    .btn-primary { background-color: var(--primary-red); color: #fff; }
    .btn-primary:hover { background-color: var(--primary-red-hover); transform: translateY(-2px); }
    .btn-secondary {
      background-color: rgba(255,255,255,0.1);
      color: #fff;
      backdrop-filter: blur(5px);
      border: 1px solid rgba(255,255,255,0.2);
    }
    .btn-secondary:hover { background-color: rgba(255,255,255,0.2); transform: translateY(-2px); }
    .btn-gold { background-color: var(--accent-gold); color: #000; }
    .btn-gold:hover { background-color: var(--accent-gold-hover); }
    .btn-danger { background-color: #dc3545; color: #fff; }
    .btn-sm { padding: 0.4rem 0.8rem; font-size: 0.875rem; }

    /* Navigation */
    .navbar {
      position: sticky;
      top: 0;
      z-index: 100;
      background-color: rgba(11, 12, 16, 0.95);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border-color);
      height: 70px;
      display: flex;
      align-items: center;
    }
    .navbar .container { display: flex; align-items: center; justify-content: space-between; }
    .nav-logo { font-size: 1.5rem; font-weight: 800; color: #fff; cursor: pointer; }
    .nav-logo span { color: var(--accent-gold); }
    .nav-links { display: flex; gap: 1.5rem; list-style: none; }
    .nav-links button {
      background: none;
      border: none;
      font-size: 1rem;
      font-weight: 500;
      color: var(--text-muted);
      cursor: pointer;
      transition: color var(--transition-fast);
    }
    .nav-links button:hover, .nav-links button.active { color: var(--accent-gold); }
    .nav-auth { display: flex; align-items: center; gap: 1rem; }

    /* Dynamic Page Visibility */
    .page-view { display: none; }
    .page-view.active { display: block; }

    /* Hero Section */
    .hero {
      position: relative;
      min-height: 500px;
      background-size: cover;
      background-position: center;
      display: flex;
      align-items: center;
      margin-bottom: 3rem;
      border-bottom: 1px solid var(--border-color);
    }
    .hero-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(90deg, var(--bg-color) 20%, rgba(11,12,16,0.7) 60%, transparent 100%),
                  linear-gradient(0deg, var(--bg-color) 0%, transparent 50%);
    }
    .hero-content { position: relative; z-index: 2; max-width: 600px; }
    .hero-badge {
      display: inline-block;
      background-color: var(--primary-red);
      color: white;
      padding: 0.25rem 0.75rem;
      font-size: 0.8rem;
      font-weight: 700;
      border-radius: var(--radius-sm);
      margin-bottom: 1rem;
      text-transform: uppercase;
    }
    .hero-title { font-size: 2.8rem; font-weight: 800; line-height: 1.1; margin-bottom: 1rem; }
    .hero-meta { display: flex; gap: 1rem; color: var(--accent-gold); font-weight: 600; margin-bottom: 1rem; }
    .hero-desc { color: var(--text-muted); margin-bottom: 2rem; font-size: 1rem; }
    .hero-actions { display: flex; gap: 1rem; }

    /* Movie Cards & Grids */
    .section-title { font-size: 1.5rem; font-weight: 700; margin-bottom: 1.5rem; display: flex; justify-content: space-between; align-items: center; }
    .section-margin { margin-bottom: 3rem; }
    .movie-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 1.5rem; }
    .movie-card {
      background-color: var(--surface-card);
      border-radius: var(--radius-md);
      overflow: hidden;
      transition: transform var(--transition-normal), box-shadow var(--transition-normal);
      border: 1px solid var(--border-color);
      display: flex;
      flex-direction: column;
    }
    .movie-card:hover { transform: translateY(-8px); box-shadow: var(--box-shadow); border-color: rgba(255, 183, 3, 0.4); }
    .poster-wrapper { position: relative; aspect-ratio: 2/3; overflow: hidden; background-color: var(--surface-color); }
    .poster-wrapper img { width: 100%; height: 100%; object-fit: cover; transition: transform var(--transition-normal); }
    .movie-card:hover .poster-wrapper img { transform: scale(1.05); }
    .movie-rating { position: absolute; top: 10px; right: 10px; background: rgba(0,0,0,0.8); color: var(--accent-gold); padding: 0.2rem 0.5rem; border-radius: var(--radius-sm); font-size: 0.8rem; font-weight: 700; }
    .movie-card-body { padding: 1rem; display: flex; flex-direction: column; flex: 1; }
    .movie-card-title { font-size: 1rem; font-weight: 700; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; margin-bottom: 0.25rem; }
    .movie-card-meta { display: flex; justify-content: space-between; color: var(--text-muted); font-size: 0.85rem; margin-top: auto; }

    /* Filters */
    .filter-bar {
      background-color: var(--surface-color);
      padding: 1rem;
      border-radius: var(--radius-md);
      margin-bottom: 2rem;
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      border: 1px solid var(--border-color);
    }
    .filter-input, .filter-select {
      background-color: var(--bg-color);
      border: 1px solid var(--border-color);
      color: #fff;
      padding: 0.6rem 1rem;
      border-radius: var(--radius-sm);
      outline: none;
    }
    .filter-input { flex: 1; min-width: 200px; }

    /* Movie Details Layout */
    .details-wrapper { display: grid; grid-template-columns: 300px 1fr; gap: 2.5rem; margin: 2rem 0; }
    .details-poster { border-radius: var(--radius-lg); overflow: hidden; border: 1px solid var(--border-color); box-shadow: var(--box-shadow); }
    .details-info h1 { font-size: 2.5rem; margin-bottom: 0.5rem; }
    .details-meta-list { display: flex; gap: 1.5rem; margin-bottom: 1.5rem; color: var(--accent-gold); font-weight: 600; }
    .details-desc { font-size: 1.1rem; color: var(--text-muted); margin-bottom: 2rem; line-height: 1.7; }
    .details-actions { display: flex; gap: 1rem; }

    /* Forms & Auth */
    .auth-container { max-width: 420px; margin: 3rem auto; background-color: var(--surface-color); padding: 2.5rem; border-radius: var(--radius-lg); border: 1px solid var(--border-color); box-shadow: var(--box-shadow); }
    .auth-title { font-size: 1.8rem; font-weight: 700; margin-bottom: 0.5rem; text-align: center; }
    .auth-subtitle { text-align: center; color: var(--text-muted); margin-bottom: 2rem; font-size: 0.9rem; }
    .form-group { margin-bottom: 1.25rem; }
    .form-group label { display: block; font-size: 0.875rem; font-weight: 600; margin-bottom: 0.5rem; }
    .form-control { width: 100%; padding: 0.75rem 1rem; background-color: var(--bg-color); border: 1px solid var(--border-color); border-radius: var(--radius-sm); color: #fff; outline: none; }
    .form-control:focus { border-color: var(--accent-gold); }

    /* Dashboard & Admin */
    .dashboard-grid { display: grid; grid-template-columns: 260px 1fr; gap: 2rem; margin: 2rem 0; }
    .dashboard-sidebar { background-color: var(--surface-color); border-radius: var(--radius-md); padding: 1.5rem; border: 1px solid var(--border-color); height: fit-content; }
    .user-profile-summary { text-align: center; padding-bottom: 1.5rem; border-bottom: 1px solid var(--border-color); margin-bottom: 1.5rem; }
    .user-avatar { width: 80px; height: 80px; border-radius: 50%; background-color: var(--primary-red); color: #fff; display: flex; align-items: center; justify-content: center; font-size: 2rem; font-weight: 700; margin: 0 auto 1rem; }
    
    .stats-cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1.5rem; margin-bottom: 2rem; }
    .stat-card { background-color: var(--surface-color); border: 1px solid var(--border-color); padding: 1.5rem; border-radius: var(--radius-md); }
    .stat-card h3 { font-size: 2rem; color: var(--accent-gold); }

    .admin-table { width: 100%; border-collapse: collapse; background-color: var(--surface-color); border-radius: var(--radius-md); overflow: hidden; border: 1px solid var(--border-color); }
    .admin-table th, .admin-table td { padding: 1rem; text-align: left; border-bottom: 1px solid var(--border-color); }
    .admin-table th { background-color: var(--surface-card); color: var(--accent-gold); }

    /* Modal */
    .modal { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.85); backdrop-filter: blur(5px); z-index: 1000; align-items: center; justify-content: center; padding: 1rem; }
    .modal.active { display: flex; }
    .modal-content { background-color: var(--surface-color); border: 1px solid var(--border-color); border-radius: var(--radius-lg); width: 100%; max-width: 600px; padding: 2rem; position: relative; max-height: 90vh; overflow-y: auto; }
    .modal-close { position: absolute; top: 1rem; right: 1rem; background: none; border: none; color: var(--text-muted); font-size: 1.5rem; cursor: pointer; }

    /* Footer & Responsive */
    .footer { background-color: var(--surface-color); border-top: 1px solid var(--border-color); padding: 2rem 0; margin-top: 4rem; text-align: center; color: var(--text-muted); font-size: 0.875rem; }
    @media (max-width: 768px) {
      .nav-links { display: none; }
      .details-wrapper, .dashboard-grid { grid-template-columns: 1fr; }
      .hero-title { font-size: 2rem; }
    }
  </style>
</head>
<body>

  <!-- Top Navigation Bar -->
  <nav class="navbar">
    <div class="container">
      <div class="nav-logo" onclick="navigateTo('home')">FIESTA <span>FILMS</span></div>
      <ul class="nav-links">
        <li><button id="nav-home" class="active" onclick="navigateTo('home')">Home</button></li>
        <li><button id="nav-movies" onclick="navigateTo('movies')">Movies</button></li>
        <li><button id="nav-dashboard" onclick="navigateTo('dashboard')">Dashboard</button></li>
        <li><button id="nav-admin" onclick="navigateTo('admin')">Admin Panel</button></li>
      </ul>
      <div class="nav-auth" id="navbar-auth"></div>
    </div>
  </nav>

  <!-- Page Content Holder -->
  <main class="main-content">

    <!-- 1. HOME PAGE VIEW -->
    <div id="page-home" class="page-view active">
      <section class="hero" id="hero-banner">
        <div class="hero-overlay"></div>
        <div class="container">
          <div class="hero-content">
            <span class="hero-badge">Featured Rwandan Film</span>
            <h1 class="hero-title" id="hero-title">The 600</h1>
            <div class="hero-meta">
              <span id="hero-rating">★ 4.8</span>
              <span id="hero-genre">Documentary</span>
              <span id="hero-year">2019</span>
            </div>
            <p class="hero-desc" id="hero-desc">The inspiring true story of a battalion surrounded behind enemy lines in Kigali who executed a daring rescue mission.</p>
            <div class="hero-actions">
              <button class="btn btn-primary" onclick="openMovieDetails('1')">Watch Now</button>
              <button class="btn btn-secondary" onclick="navigateTo('movies')">Explore All</button>
            </div>
          </div>
        </div>
      </section>

      <div class="container">
        <section class="section-margin">
          <div class="section-title">
            <h2>Trending Now</h2>
            <button class="btn btn-sm btn-secondary" onclick="navigateTo('movies')">View All</button>
          </div>
          <div class="movie-grid" id="trending-grid"></div>
        </section>

        <section class="section-margin">
          <div class="section-title">
            <h2>Latest Releases</h2>
          </div>
          <div class="movie-grid" id="latest-grid"></div>
        </section>
      </div>
    </div>

    <!-- 2. MOVIES EXPLORE VIEW -->
    <div id="page-movies" class="page-view container" style="padding-top: 2rem;">
      <h1 style="margin-bottom: 1.5rem;">Explore Rwandan Cinema</h1>
      <div class="filter-bar">
        <input type="text" id="search-input" class="filter-input" placeholder="Search by title or description...">
        <select id="genre-select" class="filter-select">
          <option value="">All Genres</option>
          <option value="Drama">Drama</option>
          <option value="Documentary">Documentary</option>
          <option value="Sci-Fi">Sci-Fi</option>
          <option value="Action">Action</option>
        </select>
        <select id="year-select" class="filter-select">
          <option value="">All Years</option>
          <option value="2022">2022</option>
          <option value="2021">2021</option>
          <option value="2019">2019</option>
          <option value="2018">2018</option>
        </select>
      </div>
      <div class="movie-grid" id="catalog-grid"></div>
    </div>

    <!-- 3. MOVIE DETAILS VIEW -->
    <div id="page-details" class="page-view container" style="padding-top: 2rem;">
      <div id="movie-details-content"></div>
      <section class="section-margin" style="margin-top: 4rem;">
        <div class="section-title">
          <h2>Related Movies</h2>
        </div>
        <div class="movie-grid" id="related-grid"></div>
      </section>
    </div>

    <!-- 4. LOGIN VIEW -->
    <div id="page-login" class="page-view">
      <div class="auth-container">
        <h2 class="auth-title">Welcome Back</h2>
        <p class="auth-subtitle">Sign in to enjoy unlimited streaming</p>
        <form id="login-form">
          <div class="form-group">
            <label>Email Address</label>
            <input type="email" id="login-email" class="form-control" placeholder="user@rwanda.rw" required>
          </div>
          <div class="form-group">
            <label>Password</label>
            <input type="password" class="form-control" placeholder="••••••••" required>
          </div>
          <button type="submit" class="btn btn-primary" style="width: 100%;">Sign In</button>
        </form>
        <p style="text-align: center; margin-top: 1rem; color: var(--text-muted);">
          Don't have an account? <a href="#" class="text-gold" onclick="navigateTo('signup')">Sign Up</a>
        </p>
      </div>
    </div>

    <!-- 5. SIGNUP VIEW -->
    <div id="page-signup" class="page-view">
      <div class="auth-container">
        <h2 class="auth-title">Create Account</h2>
        <p class="auth-subtitle">Join Fiesta Films for Rwandan Movies</p>
        <form id="signup-form">
          <div class="form-group">
            <label>Full Name</label>
            <input type="text" id="signup-name" class="form-control" placeholder="Mutesi Keza" required>
          </div>
          <div class="form-group">
            <label>Email Address</label>
            <input type="email" id="signup-email" class="form-control" placeholder="mutesi@domain.rw" required>
          </div>
          <div class="form-group">
            <label>Password</label>
            <input type="password" class="form-control" required>
          </div>
          <button type="submit" class="btn btn-gold" style="width: 100%;">Create Account</button>
        </form>
        <p style="text-align: center; margin-top: 1rem; color: var(--text-muted);">
          Already registered? <a href="#" class="text-gold" onclick="navigateTo('login')">Sign In</a>
        </p>
      </div>
    </div>

    <!-- 6. DASHBOARD VIEW -->
    <div id="page-dashboard" class="page-view container" style="padding-top: 2rem;">
      <div class="dashboard-grid">
        <aside class="dashboard-sidebar">
          <div class="user-profile-summary">
            <div class="user-avatar" id="avatar-icon">U</div>
            <h3 id="user-display-name">User Name</h3>
            <p id="user-display-email" class="text-muted" style="font-size: 0.85rem;">user@domain.rw</p>
          </div>
        </aside>
        <section>
          <h2 style="margin-bottom: 1.5rem;">❤️ My Favorites</h2>
          <div class="movie-grid" id="favorites-grid"></div>
        </section>
      </div>
    </div>

    <!-- 7. ADMIN DASHBOARD VIEW -->
    <div id="page-admin" class="page-view container" style="padding-top: 2rem;">
      <div class="stats-cards">
        <div class="stat-card">
          <h3 id="stat-total">0</h3>
          <p>Total Movies</p>
        </div>
        <div class="stat-card">
          <h3 id="stat-genres">0</h3>
          <p>Genres Available</p>
        </div>
      </div>
      <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem;">
        <h2>Movie Catalog Management</h2>
        <button class="btn btn-gold" onclick="openAdminModal()">+ Add New Movie</button>
      </div>
      <table class="admin-table">
        <thead>
          <tr>
            <th>Poster</th>
            <th>Title</th>
            <th>Genre</th>
            <th>Year</th>
            <th>Rating</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody id="admin-table-body"></tbody>
      </table>
    </div>

  </main>

  <!-- Video Watch Modal -->
  <div class="modal" id="video-modal">
    <div class="modal-content" style="max-width: 800px; padding: 0; background: #000;">
      <button class="modal-close" onclick="closeModal('video-modal')" style="color:#fff; z-index:10;">&times;</button>
      <div style="position: relative; padding-bottom: 56.25%; height: 0;">
        <iframe id="video-frame" style="position: absolute; top:0; left:0; width:100%; height:100%; border:0;" allowfullscreen></iframe>
      </div>
    </div>
  </div>

  <!-- Admin Add/Edit Modal -->
  <div class="modal" id="admin-modal">
    <div class="modal-content">
      <button class="modal-close" onclick="closeModal('admin-modal')">&times;</button>
      <h3 style="margin-bottom: 1rem;" id="modal-title">Add New Movie</h3>
      <form id="movie-form">
        <input type="hidden" id="movie-id">
        <div class="form-group">
          <label>Movie Title</label>
          <input type="text" id="form-title" class="form-control" required>
        </div>
        <div class="form-group">
          <label>Poster URL</label>
          <input type="url" id="form-poster" class="form-control" required>
        </div>
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
          <div class="form-group">
            <label>Genre</label>
            <input type="text" id="form-genre" class="form-control" required>
          </div>
          <div class="form-group">
            <label>Release Year</label>
            <input type="number" id="form-year" class="form-control" required>
          </div>
        </div>
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
          <div class="form-group">
            <label>Rating</label>
            <input type="number" step="0.1" id="form-rating" class="form-control" required>
          </div>
          <div class="form-group">
            <label>Duration</label>
            <input type="text" id="form-duration" class="form-control" placeholder="105 min" required>
          </div>
        </div>
        <div class="form-group">
          <label>Description</label>
          <textarea id="form-desc" class="form-control" rows="3" required></textarea>
        </div>
        <button type="submit" class="btn btn-primary" style="width: 100%;">Save Movie</button>
      </form>
    </div>
  </div>

  <footer class="footer">
    <div class="container">
      <p>&copy; 2026 Fiesta Films. All Rights Reserved. Rwandan Cinema Streaming.</p>
    </div>
  </footer>

  <!-- Combined JavaScript Engine -->
  <script>
    const INITIAL_MOVIES = [
      { id: "1", title: "The 600", genre: "Documentary", year: 2019, rating: 4.8, duration: "114 min", poster: "https://images.unsplash.com/photo-1536440136628-849c177e76a1?auto=format&fit=crop&w=600&q=80", description: "The true story of a battalion surrounded behind enemy lines in Kigali who executed a daring rescue mission.", videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ" },
      { id: "2", title: "Neptune Frost", genre: "Sci-Fi", year: 2021, rating: 4.6, duration: "105 min", poster: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?auto=format&fit=crop&w=600&q=80", description: "An Afrofuturist sci-fi musical set in Rwanda, following an anti-colonialist hacker collective.", videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ" },
      { id: "3", title: "Trees of Peace", genre: "Drama", year: 2022, rating: 4.7, duration: "130 min", poster: "https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=600&q=80", description: "Four women from different backgrounds forge an unbreakable sisterhood during events in Rwanda.", videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ" },
      { id: "4", title: "Nameless (A Kivu Story)", genre: "Drama", year: 2021, rating: 4.3, duration: "84 min", poster: "https://images.unsplash.com/photo-1478720568477-152d9b164e26?auto=format&fit=crop&w=600&q=80", description: "Set in Kigali, two young people face the harsh realities and struggles of modern urban youth.", videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ" }
    ];

    function getMovies() { return JSON.parse(localStorage.getItem('ff_movies')) || INITIAL_MOVIES; }
    function setMovies(movies) { localStorage.setItem('ff_movies', JSON.stringify(movies)); }
    function getFavorites() { return JSON.parse(localStorage.getItem('ff_favorites')) || []; }
    function getSession() { return JSON.parse(localStorage.getItem('ff_session')); }

    function navigateTo(pageId) {
      document.querySelectorAll('.page-view').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.nav-links button').forEach(el => el.classList.remove('active'));
      
      const targetPage = document.getElementById(`page-${pageId}`);
      if(targetPage) targetPage.classList.add('active');
      
      const targetNav = document.getElementById(`nav-${pageId}`);
      if(targetNav) targetNav.classList.add('active');

      if (pageId === 'home') renderHome();
      if (pageId === 'movies') renderCatalog();
      if (pageId === 'dashboard') renderDashboard();
      if (pageId === 'admin') renderAdmin();
    }

    function createMovieCard(movie) {
      return `
        <div class="movie-card">
          <div class="poster-wrapper">
            <img src="${movie.poster}" alt="${movie.title}">
            <span class="movie-rating">★ ${movie.rating}</span>
          </div>
          <div class="movie-card-body">
            <h3 class="movie-card-title">${movie.title}</h3>
            <div class="movie-card-meta"><span>${movie.genre}</span><span>${movie.year}</span></div>
            <button onclick="openMovieDetails('${movie.id}')" class="btn btn-primary btn-sm" style="margin-top:0.8rem; width:100%;">Details</button>
          </div>
        </div>
      `;
    }

    function renderHome() {
      const movies = getMovies();
      document.getElementById('trending-grid').innerHTML = movies.slice(0, 3).map(createMovieCard).join('');
      document.getElementById('latest-grid').innerHTML = movies.map(createMovieCard).join('');
    }

    function renderCatalog() {
      const movies = getMovies();
      const search = document.getElementById('search-input').value.toLowerCase();
      const genre = document.getElementById('genre-select').value;
      const year = document.getElementById('year-select').value;

      const filtered = movies.filter(m => {
        return (m.title.toLowerCase().includes(search) || m.description.toLowerCase().includes(search)) &&
               (!genre || m.genre === genre) &&
               (!year || m.year.toString() === year);
      });

      document.getElementById('catalog-grid').innerHTML = filtered.map(createMovieCard).join('');
    }

    function openMovieDetails(id) {
      const movie = getMovies().find(m => m.id === id) || getMovies()[0];
      const favs = getFavorites();
      const isFav = favs.includes(movie.id);

      document.getElementById('movie-details-content').innerHTML = `
        <div class="details-wrapper">
          <div class="details-poster"><img src="${movie.poster}"></div>
          <div class="details-info">
            <h1>${movie.title}</h1>
            <div class="details-meta-list">
              <span>★ ${movie.rating}</span><span>${movie.genre}</span><span>${movie.year}</span><span>${movie.duration}</span>
            </div>
            <p class="details-desc">${movie.description}</p>
            <div class="details-actions">
              <button class="btn btn-primary" onclick="watchMovie('${movie.videoUrl}')">▶ Watch Now</button>
              <button class="btn btn-secondary" onclick="toggleFav('${movie.id}')">${isFav ? '❤️ Saved' : '🤍 Add to Favorites'}</button>
            </div>
          </div>
        </div>
      `;

      const related = getMovies().filter(m => m.genre === movie.genre && m.id !== movie.id);
      document.getElementById('related-grid').innerHTML = related.map(createMovieCard).join('');
      navigateTo('details');
    }

    function watchMovie(url) {
      document.getElementById('video-frame').src = url;
      document.getElementById('video-modal').classList.add('active');
    }

    function closeModal(id) {
      document.getElementById(id).classList.remove('active');
      if(id === 'video-modal') document.getElementById('video-frame').src = '';
    }

    function toggleFav(id) {
      let favs = getFavorites();
      if (favs.includes(id)) favs = favs.filter(f => f !== id);
      else favs.push(id);
      localStorage.setItem('ff_favorites', JSON.stringify(favs));
      openMovieDetails(id);
    }

    function renderDashboard() {
      const user = getSession();
      if(!user) { navigateTo('login'); return; }
      
      document.getElementById('user-display-name').textContent = user.name;
      document.getElementById('user-display-email').textContent = user.email;
      document.getElementById('avatar-icon').textContent = user.name.charAt(0).toUpperCase();

      const favs = getFavorites();
      const movies = getMovies().filter(m => favs.includes(m.id));
      document.getElementById('favorites-grid').innerHTML = movies.length ? movies.map(createMovieCard).join('') : '<p class="text-muted">No favorites saved.</p>';
    }

    function renderAdmin() {
      const movies = getMovies();
      document.getElementById('stat-total').textContent = movies.length;
      document.getElementById('stat-genres').textContent = new Set(movies.map(m => m.genre)).size;

      document.getElementById('admin-table-body').innerHTML = movies.map(m => `
        <tr>
          <td><img src="${m.poster}" style="width:30px; height:45px; object-fit:cover;"></td>
          <td><strong>${m.title}</strong></td>
          <td>${m.genre}</td>
          <td>${m.year}</td>
          <td>★ ${m.rating}</td>
          <td><button class="btn btn-danger btn-sm" onclick="deleteMovie('${m.id}')">Delete</button></td>
        </tr>
      `).join('');
    }

    function deleteMovie(id) {
      setMovies(getMovies().filter(m => m.id !== id));
      renderAdmin();
    }

    function openAdminModal() {
      document.getElementById('admin-modal').classList.add('active');
    }

    // Forms Handlers
    document.getElementById('login-form').addEventListener('submit', (e) => {
      e.preventDefault();
      const email = document.getElementById('login-email').value;
      localStorage.setItem('ff_session', JSON.stringify({ name: email.split('@')[0], email }));
      updateAuthUI();
      navigateTo('dashboard');
    });

    document.getElementById('signup-form').addEventListener('submit', (e) => {
      e.preventDefault();
      const name = document.getElementById('signup-name').value;
      const email = document.getElementById('signup-email').value;
      localStorage.setItem('ff_session', JSON.stringify({ name, email }));
      updateAuthUI();
      navigateTo('dashboard');
    });

    document.getElementById('movie-form').addEventListener('submit', (e) => {
      e.preventDefault();
      const movies = getMovies();
      movies.unshift({
        id: Date.now().toString(),
        title: document.getElementById('form-title').value,
        poster: document.getElementById('form-poster').value,
        genre: document.getElementById('form-genre').value,
        year: parseInt(document.getElementById('form-year').value),
        rating: parseFloat(document.getElementById('form-rating').value),
        duration: document.getElementById('form-duration').value,
        description: document.getElementById('form-desc').value,
        videoUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ"
      });
      setMovies(movies);
      closeModal('admin-modal');
      renderAdmin();
    });

    function updateAuthUI() {
      const user = getSession();
      const container = document.getElementById('navbar-auth');
      if (user) {
        container.innerHTML = `<button onclick="logout()" class="btn btn-danger btn-sm">Logout</button>`;
      } else {
        container.innerHTML = `<button onclick="navigateTo('login')" class="btn btn-gold btn-sm">Login</button>`;
      }
    }

    function logout() {
      localStorage.removeItem('ff_session');
      updateAuthUI();
      navigateTo('home');
    }

    // Filters Live Event Listeners
    document.getElementById('search-input').addEventListener('input', renderCatalog);
    document.getElementById('genre-select').addEventListener('change', renderCatalog);
    document.getElementById('year-select').addEventListener('change', renderCatalog);

    // Initial Load Setup
    if (!localStorage.getItem('ff_movies')) setMovies(INITIAL_MOVIES);
    updateAuthUI();
    renderHome();
  </script>
</body>
</html>
