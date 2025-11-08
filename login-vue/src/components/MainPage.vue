<template>
  <div class="post-page">
    <aside class="sidebar" aria-label="Main menu">
      <ul>
        <li>
          <button class="menu-btn" title="Profile">
            <img :src="man" alt="Profile" />
            <span>Profile</span>
          </button>
        </li>
        <li>
          <button class="menu-btn" title="Settings">
            <img :src="gear" alt="Settings" />
            <span>Settings</span>
          </button>
        </li>
        <li>
          <button class="menu-btn" title="Logout">
            <img :src="exitIcon" alt="Logout" />
            <span>Logout</span>
          </button>
        </li>
      </ul>
    </aside>
    <div class="main-area">
      <header class="topbar" role="banner" aria-label="Top menu">
        <div class="topbar-left">
          <strong>DockX</strong>
        </div>
        <nav class="topbar-nav" aria-label="Secondary navigation">
          <button class="icon-btn">Home</button>
          <button class="icon-btn">Help</button>
        </nav>
        <div class="topbar-right">Benvenuto</div>
      </header>
    </div>
  </div>
</template>

<script setup lang="ts">
import man from '../assets/man.svg'
import gear from '../assets/gear.svg'
import exitIcon from '../assets/exit.svg'
</script>

<style scoped>
.post-page {
  position: fixed;
  inset: 0; /* top:0; right:0; bottom:0; left:0 */
  display: flex;
  align-items: flex-start;
  padding: 1.25rem;
  background: #f3f4f6;
  z-index: 1000;
}
.sidebar {
  width: 96px;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 6px 18px rgba(15,23,42,0.06);
  padding: 0.75rem;
  height: 100%;
  align-self: stretch;
}
.sidebar ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  height: 100%;
  justify-content: center; /* center the list vertically */
  align-items: center; /* center items horizontally */
}
.menu-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.35rem;
  background: transparent;
  border: none;
  cursor: pointer;
  width: 100%;
  padding: 0.4rem 0;
}
.menu-btn img {
  width: 40px;
  height: 40px;
  display: block;
  object-fit: contain;
}
.menu-btn span {
  font-size: 0.75rem;
  color: #374151;
  text-align: center;
}
.menu-btn:hover,
.menu-btn:focus-visible {
  background: rgba(99,102,241,0.08);
  border-radius: 8px;
  outline: none;
}

@media (max-width: 640px) {
  .post-page { justify-content: center }
}

.main-area {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 1rem 1.25rem;
}
.topbar {
  height: 56px;
  background: #fff;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1rem;
  box-shadow: 0 6px 18px rgba(15,23,42,0.06);
}
.topbar-left { font-size: 1rem; color: #111827 }
.topbar-right { font-size: 0.95rem; color: #374151 }
.topbar-nav { display:flex; gap:0.5rem }
.icon-btn { background: transparent; border: none; padding: 0.35rem 0.6rem; border-radius:6px; cursor:pointer }
.icon-btn:hover, .icon-btn:focus-visible { background: rgba(15,23,42,0.04) }
</style>
