<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/search">Search</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
  @import './assets/styles/main.css';
</style>
