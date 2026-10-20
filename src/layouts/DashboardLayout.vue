<script setup lang="ts">
import { RouterView, RouterLink } from 'vue-router'
</script>

<template>
  <!-- RAIL & PANE SYSTEM -->
  <div class="dashboard-layout">
    <!-- Sidebar Navigation -->
    <aside class="dashboard-rail">
      <div class="rail-brand">
        <RouterLink to="/">Gatherly Organizer</RouterLink>
      </div>

      <nav class="rail-nav">
        <RouterLink to="/dashboard" class="rail-link" exact-active-class="active">
          Dashboard
        </RouterLink>

        <RouterLink to="/dashboard/events" class="rail-link" active-class="active">
          Event Management
        </RouterLink>
      </nav>

      <div class="rail-footer">
        <RouterLink to="/" class="rail-link"> &larr; Back to Public </RouterLink>
      </div>
    </aside>

    <!-- Main Content -->
    <main class="dashboard-pane">
      <header class="pane-header">
        <h1>Dashboard</h1>
        <div class="user-profile">Admin</div>
      </header>

      <div class="pane-content">
        <RouterView />
      </div>
    </main>
  </div>
</template>

<style scoped>
/* Main Layout */
.dashboard-layout {
  display: flex;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  background-color: var(--bg-gray, #f5f5fa);
  font-family: Arial, sans-serif;
}

/* Sidebar */
.dashboard-rail {
  display: flex;
  flex-direction: column;
  flex-shrink: 0;
  width: 260px;
  height: 100%;
  background-color: #1c1948;
  color: white;
}

.rail-brand {
  padding: 24px;
  font-size: 1.2rem;
  font-weight: 700;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.rail-brand a {
  color: white;
  text-decoration: none;
}

.rail-nav {
  display: flex;
  flex: 1;
  flex-direction: column;
  padding: 24px 0;
}

.rail-link {
  display: block;
  padding: 12px 24px;
  color: #a0a0be;
  font-weight: 500;
  text-decoration: none;
  border-left: 4px solid transparent;
  transition:
    background 0.2s ease,
    color 0.2s ease;
}

.rail-link:hover {
  background-color: rgba(255, 255, 255, 0.06);
  color: white;
}

.rail-link.active {
  background-color: rgba(255, 255, 255, 0.08);
  color: white;
  border-left-color: var(--primary, #a78bfa);
}

.rail-footer {
  padding: 16px 0;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

/* Main Pane */
.dashboard-pane {
  display: flex;
  flex: 1;
  flex-direction: column;
  min-width: 0;
  height: 100%;
  overflow-y: auto;
}

.pane-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 32px;
  background-color: white;
  border-bottom: 1px solid var(--border-color, #e5e5ef);
}

.pane-header h1 {
  margin: 0;
  color: #302b46;
  font-size: 1.5rem;
}

.user-profile {
  padding: 10px 16px;
  border-radius: 12px;
  background-color: #f0eafa;
  color: #6845a0;
  font-size: 0.9rem;
  font-weight: 600;
}

.pane-content {
  flex: 1;
  padding: 32px;
}

/* Responsive Layout */
@media (max-width: 768px) {
  .dashboard-layout {
    flex-direction: column;
    height: 100vh;
    overflow: auto;
  }

  .dashboard-rail {
    width: 100%;
    height: auto;
  }

  .rail-brand {
    padding: 18px 20px;
  }

  .rail-nav {
    flex-direction: row;
    padding: 8px;
    gap: 4px;
  }

  .rail-link {
    padding: 12px;
    border-left: none;
    border-radius: 8px;
    font-size: 12px;
  }

  .rail-link.active {
    border-left-color: transparent;
    background-color: rgba(255, 255, 255, 0.12);
  }

  .rail-footer {
    display: none;
  }

  .dashboard-pane {
    overflow: visible;
  }

  .pane-header {
    padding: 18px;
  }

  .pane-content {
    padding: 18px;
  }
}
</style>
