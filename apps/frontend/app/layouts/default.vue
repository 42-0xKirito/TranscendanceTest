<script setup>
    import { ref } from 'vue'

    const profileOpen = ref(false)

    function toggleProfile() {
    profileOpen.value = !profileOpen.value
    }

    function button1() {
    navigateTo('/')
    }

    function button2() {
    console.log("Button 2");
    }

    function button3() {
    navigateTo('/profil')
    }
</script>

<template>
  <div>
    <header class="header">
      <p>Mon site</p>
      <button class="profil-button" @click="toggleProfile()">👤</button>
      <button class="home-button" @click="navigateTo('/')">🏠</button>
    </header>

    <div class="hotbar">
        <button class="hotbar-button" @click="button1">
        🏠
        </button>

        <button class="hotbar-button" @click="button2">
        ⚙️
        </button>

        <button class="hotbar-button" @click="button3">
        👤
        </button>
  </div>

  <main>
    <slot />
  </main>

    <aside class="profile-panel" :class="{ open: profileOpen }">

      <div class="profile-card">
        Profile
      </div>

      <div class="profile-card">
        Settings
      </div>

      <div class="profile-card">
        Account
      </div>

      <div class="profile-card">
        Logout
      </div>
    </aside>
  </div>
</template>

<style>

.hotbar {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);

  display: flex;
  gap: 20px;

  padding: 10px;

  background-color: #252525;
  border: 1px solid #444;
  border-radius: 15px;

  z-index: 3000;
}

.hotbar-button {
  width: 50px;
  height: 50px;

  background: none;
  border: 2px solid transparent;
  border-radius: 10px;

  color: white;
  font-size: 24px;

  cursor: pointer;

  transition: transform 0.15s, border 0.15s, box-shadow 0.15s;
}

.hotbar-button:hover {
  border: 2px solid white;
  transform: translateY(-3px);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.4);
}

.hotbar-button:active {
  transform: scale(0.9);
}

html,
body {
    margin: 0;
    background-color: #1e1e1e;
    color: white;
}

.app {
    min-height: 100vh;
    background-color: #1e1e1e;
}

.header {
  position: fixed;
  top: 0;
  left: 0;

  width: 100%;
  height: 60px;

  background-color: #252525;
  color: white;

  display: flex;
  align-items: center;
  justify-content: center;

  z-index: 3000;
}

.home-button {
    position: absolute;
    left: 0px;

    background: none;
    color: white;
    border: 2px solid transparent;
    border-radius: 10px;
    padding: 8px 15px;

    cursor: pointer;
}

.home-button:hover {
    border: 2px solid white;
}

.home-button:active {
    transform: scale(0.9);
}

.profil-button {
  position: absolute;
  right: 0px;

  background: none;
  color: white;
  border: 2px solid transparent;
  border-radius: 10px;
  padding: 8px 15px;

  cursor: pointer;
}

.profil-button:hover {
  border: 2px solid white;
}

.profil-button:active {
  transform: scale(0.9);
}

.profile-panel {
  position: fixed;

  top: 60px;
  right: 0;

  width: 350px;
  height: calc(100vh - 60px);

  background-color: #1e1e1e;
  border-left: 2px solid #444;

  padding: 30px;
  box-sizing: border-box;

  transform: translateX(100%);
  transition: transform 0.3s ease;

  z-index: 2000;
}

.profile-panel.open {
  transform: translateX(0);
}

.profile-card {
  height: 100px;

  margin-bottom: 20px;

  background-color: #252525;
  border: 2px solid #444;
  border-radius: 15px;

  display: flex;
  align-items: center;
  justify-content: center;

  color: white;

  cursor: pointer;

  transition: transform 0.1s, box-shadow 0.1s;
}

.profile-card:hover {
    transform: translateX(5px) translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0, 0.7);
}
</style>