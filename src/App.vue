<template>
  <div class="app">
    <ChatWindow />
    <SettingsDialog :is-open="showSettings" @close="showSettings = false" />
    <div class="about-bar">
      <div class="about-section">
        <span class="github-icon"></span>
        <a href="https://github.com/senzi/win98-llm-chat" target="_blank">GitHub</a>
      </div>
      <div class="about-separator"></div>
      <div class="about-section">
        <span>MIT License</span>
      </div>
      <div class="about-separator"></div>
      <div class="about-section">
        <span>作者：Windsurf & sennzi</span>
      </div>
      <div class="about-section" style="margin-left: auto;">
        <span>v1.0.0</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, provide } from 'vue'
import ChatWindow from './components/ChatWindow.vue'
import SettingsDialog from './components/SettingsDialog.vue'

const showSettings = ref(false)

const openSettings = () => {
  showSettings.value = true
}

provide('openSettings', openSettings)

defineExpose({
  openSettings
})
</script>

<style>
@import '98.css';

html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: "Microsoft Sans Serif", "Segoe UI", sans-serif;
}

.app {
  min-height: 100vh;
  background: #008080;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.about-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 28px;
  background: #c0c0c0;
  border-top: 1px solid #ffffff;
  border-bottom: 1px solid #404040;
  padding: 2px 4px;
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 11px;
  font-family: "Microsoft Sans Serif", Tahoma, sans-serif;
  z-index: 9999;
}

.about-section {
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 0 8px;
  height: 20px;
  background: #c0c0c0;
}

.about-section a {
  color: #000080;
  text-decoration: none;
}

.about-section a:hover {
  text-decoration: underline;
}

.about-separator {
  width: 1px;
  height: 16px;
  background: #808080;
  border-right: 1px solid #ffffff;
}

.github-icon {
  width: 14px;
  height: 14px;
  background: url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath fill='%23000080' d='M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z'/%3E%3C/svg%3E") no-repeat center center;
  background-size: contain;
}
</style>
