<script setup lang="ts">
import { useData } from 'vitepress'

const { page, site } = useData()

const navigation = [
  { label: 'Home', href: '/', page: 'index.md' },
  { label: 'Blog', href: '/blog', page: 'blog.md' },
  { label: 'Contacts', href: '/contacts', page: 'contacts.md' },
  { label: 'Devices', href: '/devices', page: 'devices.md' }
]
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="brand" href="/" aria-label="Go to home">
        <span class="brand-avatar" aria-hidden="true">F</span>
        <span>{{ site.title }}</span>
      </a>
      <span class="header-caption">Personal portfolio</span>
    </header>

    <div class="page-frame">
      <aside class="sidebar" aria-label="Main navigation">
        <p class="sidebar-heading">Explore</p>
        <nav class="sidebar-nav">
          <a
            v-for="item in navigation"
            :key="item.href"
            :href="item.href"
            class="sidebar-link"
            :class="{ active: page.relativePath === item.page }"
            :aria-current="page.relativePath === item.page ? 'page' : undefined"
          >
            <span class="nav-indicator" aria-hidden="true"></span>
            {{ item.label }}
          </a>
        </nav>
        <div class="sidebar-note">
          <span class="status-dot" aria-hidden="true"></span>
          <span>Building things on the web</span>
        </div>
      </aside>

      <main class="main-content">
        <article class="markdown-body">
          <Content />
        </article>
        <footer class="site-footer">
          <span>Made with VitePress</span>
          <span>·</span>
          <a href="https://github.com/" target="_blank" rel="noreferrer">GitHub</a>
        </footer>
      </main>
    </div>
  </div>
</template>
