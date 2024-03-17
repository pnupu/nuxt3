<template>
  <div>
    <v-layout>
      <v-app-bar height="100px" flat>
        <Header />
      </v-app-bar>
      <v-main class="main-content">
        <slot />
      </v-main>
    </v-layout>
  </div>
</template>

<style lang="scss" scoped>
.main-content {
  padding-top: 7rem; 
  flex: 1; 
}
</style>
